```
spg_options(;verbose=3,optTol=1f-5,progTol=1f-7,
            maxIter=20,suffDec=1f-4,memory=2,
            useSpectral=true,curvilinear=false,
            feasibleInit=false,testOpt=true,
            bbType=true,testInit=false, store_trace=false,
            optNorm=Inf,iniStep=1f0, maxLinesearchIter=10)
```

スペクトラルプロジェクト勾配アルゴリズムのオプション構造。

# 引数

  * `verbose`: 冗長性のレベル (0: 出力なし, 1: イテレーション (デフォルト))
  * `optTol`: 最適性をチェックするために使用される許容誤差 (デフォルト: 1e-5)
  * `progTol`: 進捗の欠如をチェックするために使用される許容誤差 (デフォルト: 1e-9)
  * `maxIter`: 最大イテレーション数 (デフォルト: 20)
  * `suffDec`: アルミホ条件における十分な減少パラメータ (デフォルト: 1e-4)
  * `memory`: 非単調アルミホ条件で振り返るステップ数
  * `useSpectral`: 勾配方向のスペクトルスケーリングを使用する (デフォルト: 1)
  * `curvilinear`: 投影アークに沿ってバックトラックする (デフォルト: 0)
  * `testOpt`: 最適性条件をテストする (デフォルト: 1)
  * `feasibleInit`: 1の場合、初期点は実行可能であると仮定される
  * `bbType`: バルジライ・ボルウェインステップのタイプ (デフォルト: 1)
  * `testInit`: 最適性のために初期推定をテストするかどうか (デフォルト: false)
  * `store_trace`: xのトレース/履歴を保存するかどうか (デフォルト: false)
  * `optNorm`: 一次最適性条件のノルム (デフォルト: Inf)
  * `iniStep`: 初期ステップ長の推定 (デフォルト: 1)
  * `maxLinesearchIter`: 最大ラインサーチイテレーション数 (デフォルト: 20)
