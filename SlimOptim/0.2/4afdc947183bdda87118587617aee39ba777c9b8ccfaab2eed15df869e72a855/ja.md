```
pqn_options(;verbose=2, optTol=1f-5, progTol=1f-7,
            maxIter=20, suffDec=1f-4, corrections=10, adjustStep=false,
            bbInit=false, store_trace=false, SPGoptTol=1f-6, SPGprogTol=1f-7,
            SPGiters=10, SPGtestOpt=false, maxLinesearchIter=20)
```

スペクトラルプロジェクト勾配アルゴリズムのオプション構造。

# 引数

  * `verbose`: 冗長性のレベル (0: 出力なし, 1: イテレーション (デフォルト))
  * `optTol`: 最適性をチェックするために使用される許容誤差 (デフォルト: 1e-5)
  * `progTol`: 進捗をチェックするために使用される許容誤差 (デフォルト: 1e-9)
  * `maxIter`: 最大イテレーション数 (デフォルト: 20)
  * `suffDec`: アルミホ条件における十分な減少パラメータ (デフォルト: 1e-4)
  * `corrections`: 保存するlbfgs補正の数 (デフォルト: 10)
  * `adjustStep`: 線形探索の二次初期化を使用するか (デフォルト: 0)
  * `bbInit`: バルジライ-ボルウェインステップでサブプロブレムを初期化する (デフォルト: 1)
  * `store_trace`: xのトレース/履歴を保存するかどうか (デフォルト: false)
  * `SPGoptTol`: SPG方向探索のための最適性許容誤差 (デフォルト: 1e-6)
  * `SPGprogTol`: 進捗をチェックするために使用されるSPG許容誤差 (デフォルト: 1e-7)
  * `SPGiters`: SPG方向探索の最大イテレーション数 (デフォルト: 10)
  * `SPGtestOpt`: SPGで最適性をチェックするかどうか (デフォルト: false)
  * `maxLinesearchIter`: 最大線形探索イテレーション数 (デフォルト: 20)
  * `memory`: 非単調関数減少条件のためのステップ数。
  * `iniStep`: 初期ステップ長の推定 (デフォルト: 1)。adjustStepが有効な場合は無視される。
