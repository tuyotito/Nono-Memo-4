# Nono Memo — application Android

Jeux de mémoire (page web autonome) empaquetés en application Android avec [Capacitor](https://capacitorjs.com/).

## Structure

```
nono-memo/
├── www/index.html          ← l'application (fichier unique, hors-ligne)
├── assets/icon.svg         ← icône (convertie en PNG automatiquement)
├── assets/splash.svg       ← écran de démarrage
├── capacitor.config.json   ← nom et identifiant de l'app
├── package.json
└── .github/workflows/build-apk.yml   ← compile l'APK automatiquement
```

## Obtenir l'APK (sans rien installer)

1. Créez un dépôt GitHub (vide) et envoyez-y tout le contenu de ce dossier (branche `main`).
2. Ouvrez l'onglet **Actions** : la compilation démarre seule (≈ 5-8 min).
   Sinon : *Build APK Android* → **Run workflow**.
3. Une fois terminée, cliquez sur l'exécution, puis téléchargez **nono-memo-apk** en bas de page (un .zip contenant `app-debug.apk`).
4. Copiez l'APK sur le téléphone, ouvrez-le et autorisez l'installation depuis cette source.

## Modifier l'application

Éditez `www/index.html`, faites un commit : un nouvel APK est généré.

## Changer l'identité de l'app

- Nom : `appName` dans `capacitor.config.json`
- Identifiant : `appId` (ex. `com.votrenom.nonomemo`) — à fixer avant toute publication sur le Play Store, il ne pourra plus changer.

## Publier sur le Play Store (plus tard)

L'APK produit est un APK *debug* (installation directe). Pour le Play Store il faut un AAB signé avec votre propre keystore (`./gradlew bundleRelease`) ; ne committez jamais le keystore (déjà exclu par `.gitignore`).
