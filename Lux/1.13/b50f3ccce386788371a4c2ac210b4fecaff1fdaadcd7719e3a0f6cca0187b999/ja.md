```
Scale(dims, activation=identity; init_weight=ones32, init_bias=zeros32, use_bias=True())
```

非常に特定の構造（対角要素のみが非ゼロ）を持つ疎接続層を作成します。フォワードパスは次のように与えられます：`y = activation.(weight .* x .+ bias)`

## 引数

  * `dims`: 学習可能なスケールおよびバイアスパラメータのサイズ。
  * `activation`: 活性化関数

## キーワード引数

  * `init_weight`: 重み行列の初期化子（`weight = init_weight(rng, out_dims, in_dims)`）
  * `init_bias`: バイアスベクトルの初期化子（`use_bias=false`の場合は無視されます）
  * `use_bias`: この値を`false`に設定することで、学習可能なバイアスを完全に無効にできます

## 入力

  * `x`はサイズが`(dims..., B)`または`(dims...[0], ..., dims[k])`の配列でなければなりません（`k ≤ size(dims)`の場合）

## 戻り値

  * サイズが`(dims..., B)`または`(dims...[0], ..., dims[k])`の配列（`k ≤ size(dims)`の場合）
  * 空の`NamedTuple()`

## パラメータ

  * `weight`: サイズが`(dims...)`の重み配列
  * `bias`: サイズが`(dims...)`のバイアス
