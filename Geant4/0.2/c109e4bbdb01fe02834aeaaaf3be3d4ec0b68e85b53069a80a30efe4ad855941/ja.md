```
beamOn(app::G4JLApplication, nevents::Int)
```

`nevents` イベントで新しい実行を開始します。マルチスレッドの場合、関数は実行を開始する前にGCセーフ状態に入ります。

# 引数

  * `app::G4JLApplication`: Geant4 アプリケーション
  * `nevents::Int`: イベントの数
