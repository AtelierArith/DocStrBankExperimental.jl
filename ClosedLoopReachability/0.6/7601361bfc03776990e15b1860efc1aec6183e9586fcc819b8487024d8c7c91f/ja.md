```
solve(prob::AbstractControlProblem, args...; kwargs...)
```

制御問題 `prob` を解きます。

### 入力

  * `prob` – 制御された問題

追加のオプションは引数またはキーワード引数として渡されます。詳細については以下のノートを参照してください。例についてはオンラインドキュメントを参照してください。

### 出力

周期的コントローラによって制御される到達可能性問題の解。制御信号は各フローパイプの `ext` フィールドに格納されます。

### ノート

#### 必須引数

  * `tspan` キーワード引数を使用して時間範囲（開始時間と時間のホライズン）を指定します。タプル、区間、または2つのコンポーネントを持つベクトルである必要があります。あるいは、`T` キーワード引数を使用して時間のホライズンのみを指定することもでき、その場合、開始時間はゼロと見なされます。
  * `algorithm_plant` キーワード引数を使用してプラントのアルゴリズムを指定します。
  * `algorithm_controller` キーワード引数を使用してコントローラのアルゴリズムを指定します。

#### オプション引数

  * `splitter` および `input_splitter` キーワード引数を使用してスプリッタを指定します。

デフォルト: `NoSplitter()`

  * `reconstruction_method` キーワード引数を使用してプラントとコントローラの間のインターフェースの再構成方法を指定します。

デフォルト: `TaylorModelReconstructor()` ```
