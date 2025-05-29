```
initialize(app::G4JLApplication)
```

Geant4アプリケーションを初期化します。これは`G4RunManager`を初期化し、検出器のジオメトリを構築し、宣言された感度検出器を設定します。マルチスレッドの場合、関数はアプリケーションを初期化する前にGCセーフ状態に入ります。これにより、ワーカースレッドによって`build()`関数が呼び出されます。

# 引数

  * `app::G4JLApplication`: Geant4アプリケーション
