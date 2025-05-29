```
ConstrainedIndexValueResampling(constraints::NTuple{N_DATASETS, NTuple{N_VARIABLES, Union{SamplingConstraint, Vector{<:SamplingConstraint}}}}, n::Int)
```

不確実なインデックス値データセットのセットに対して制約を持つリサンプリングを実行する必要があることを示します。使用例については、以下の例を参照してください。

## フィールド

  * `constraints`。データセットの制約。制約は長さ `N_DATASETS` のタプルとして表され、`i` 番目のタプル要素は、`N_VARIABLES` 番目の異なる変数の制約を含む `N_VARIABLES` 長のタプルです。詳細については、以下の「インデクシング」を参照してください。各個別の変数の制約は、単一のサンプリング制約として、または変数の長さに一致する長さのサンプリング制約のベクトルとして提供する必要があります (`Union{SamplingConstraint, Vector{<:SamplingConstraint}}`)。たとえば、`i` 番目のデータセットの `j` 番目の変数が352の観測値を含む場合、`constraints[i, j]` は単一のサンプリング制約（例：`TruncateStd(1.1)`）または352の異なるサンプリング制約のベクトル（例：`[TruncateStd(1.0 + rand()) for i = 1:352]`）でなければなりません。
  * `n::Int`。引き出しの数。

## インデクシング

`c` が `ConstrainedIndexValueResampling` のインスタンスであると仮定します。すると、

  * `c[i]` は `i` 番目のデータセットの制約の `NTuple` を返し、
  * `c[i, j]` は `i` 番目のデータセットの `j` 番目の変数の制約を返します。

## 例

### `ConstrainedIndexValueResampling` の定義

異なるサンプリング制約を持つ3つの別々の不確実なインデックス値データセットに制約を加えたいと仮定します。

```julia
# 1番目、2番目、3番目のデータセットの (インデックス制約, 値制約)
c1 = (TruncateStd(1), TruncateStd(1.1))
c2 = (TruncateStd(0.5), TruncateQuantiles(0.1, 0.8))
c3 = (TruncateQuantiles(0.05, 0.95), TruncateQuantiles(0.33, 0.67))
c = ConstrainedIndexValueResampling(c1, c2, c3)
```

今、

  * `c[2]` は2番目のデータセットの制約の `NTuple` を返し、
  * `c[1, 2]` は1番目のデータセットの2番目の変数の制約を返します。

### 引き出しの数を制御する

引き出しの数は指定しない場合、デフォルトで1になります。1回以上の引き出しを実行する必要があることを示すには、制約をコンストラクタに供給する前に引き出しの数を入力するだけです。

```
c1 = (TruncateStd(1), TruncateStd(1.1))
c2 = (TruncateStd(0.5), TruncateQuantiles(0.1, 0.8))

# 単一の引き出し
c_single = ConstrainedIndexValueResampling(c1, c2)

# 複数の（300）引き出し
c_multiple = ConstrainedIndexValueResampling(300, c1, c2) 
```

### 詳細な例

不確実なインデックス値データセット `x` と `y` があるとしましょう。`x` と `y` の両方の時間インデックスと値の供給分布/人口に制約を加えたいとします。`x` については、平均周りの標準偏差の `0.8` 倍でインデックスを切り捨て、`y` については、平均周りの標準偏差の `1.5` 倍でインデックスを切り捨てます。次に、`x` の値をおおよそ20パーセンタイル範囲で切り捨て、`y` の値をおおよそ80パーセンタイル範囲で切り捨てます。

このすべての情報は、`ConstrainedIndexValueResampling` インスタンスに組み合わせることができます。このインスタンスは、不確実なインデックス値データセットを受け入れる任意の関数に渡すことができ、データセットを供給する分布/人口の切り捨てたバージョンでリサンプリングを実行する必要があることを示します。

```julia
# すべての供給分布/人口を正確に同じ分位数で切り捨てないようにするためのノイズ。
r = Uniform(0, 0.01)

constraints_x_inds = TruncateStd(0.8)
constraints_y_inds = TruncateStd(1.5)
constraints_x_vals = [TruncateQuantiles(0.4 + rand(r), 0.6 + rand(r)) for i = 1:length(x)];
constraints_y_vals = [TruncateQuantiles(0.1 + rand(r), 0.9 + rand(r)) for i = 1:length(x)];

cs_x = (constraints_x_inds, constraints_x_vals)
cs_y = (constraints_y_inds, constraints_y_vals)

resampling = ConstrainedIndexValueResampling(cs_x, cs_y)
```
