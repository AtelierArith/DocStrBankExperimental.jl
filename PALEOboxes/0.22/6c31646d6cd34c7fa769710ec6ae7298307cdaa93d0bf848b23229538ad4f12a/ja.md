```
PALEOboxes
```

PALEOboxesは、PALEOモデルフレームワークのためのモデルカプラーを提供します。

これは、公共のgithubリポジトリ[PALEOboxes.jl](https://github.com/PALEOtoolkit/PALEOboxes.jl)としてJuliaパッケージに登録されており、オンライン[ドキュメント](https://paleotoolkit.github.io/PALEOboxes.jl)もあります。

PALEO `Model`は`Domain`を含み、それぞれが`Field`を含む`Data`配列を定義するVariablesと、Variablesに作用してモデルの時間発展を計算する`ReactionMethod`を持つReactionsを含みます。

PALEOboxesは.yaml構成ファイルからモデルを作成し、以下のための統一メカニズムを提供するカプラーを実装します。

1. ‘低レベル’のカップリング（例：Domain内の個々のレドックス反応をリンクすること）に基づいて構築される
2. ‘モジュールレベル’のカップリング（例：大気と海洋コンポーネントをリンクすること）で、フラックスを通信するための名前を標準化し、これにより
3. 生物地球化学反応と輸送の分離が可能になります。
