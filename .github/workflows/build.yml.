name: Build APK

on:
  push:
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-java@v4
        with:
          distribution: temurin
          java-version: '17'

      - uses: android-actions/setup-android@v3

      - name: Instalar plataforma Android 33
        run: yes | sdkmanager --licenses > /dev/null; sdkmanager "platforms;android-33" "build-tools;33.0.2"

      - uses: gradle/actions/setup-gradle@v3
        with:
          gradle-version: '8.7'

      - name: Compilar APK
        run: gradle :app:assembleDebug --no-daemon

      - uses: actions/upload-artifact@v4
        with:
          name: MinimalLauncher-APK
          path: app/build/outputs/apk/debug/app-debug.apk
