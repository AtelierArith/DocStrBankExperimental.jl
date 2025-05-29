# メソッド Stanmodel

Stanmodelを作成します。

### コンストラクタ

```julia
Stanmodel(
  method=Sample();
  name="noname", 
  nchains=4,
  num_warmup=1000, 
  num_samples=1000,
  thin=1,
  model="",
  monitors=String[],
  random=Random(),
  output=Output(),
  printsummary=false,
  pdir::String=pwd(),
  tmpdir::String=joinpath(pwd(), "tmp"),
  output_format=:array
)

```

### 必須引数

```julia
* `method::Method`             : See ?Method
```

### オプション引数

```julia
* `name::String`               : モデルの名前
* `nchains::Int`               : チェーンの数
* `num_warmup::Int`            : num_warmupに使用されるサンプルの数
* `num_samples::Int`           : サンプルの反復回数
* `thin::Int`                  : Stanのスリム化係数
* `model::String`              : Stanプログラムソース
* `monitors::String[] `        : ポストプロセッシングのために保存される変数
* `random::Random`             : ランダムシード設定
* `output::Output`             : ファイル出力オプション
* `printsummary=true`          : 計算されたスタンの要約を表示
* `pdir::String`               : 作業ディレクトリ
* `tmpdir::String`             : 出力ファイルが保存されるディレクトリ
* `output_format::Symbol `     : 出力形式
```

### CmdStan.jlは3つのoutput_format値をサポートしています：

```julia
1. :array           # ドローの配列を返す（デフォルト）
2. :mcmcchains      # MCMCChains.Chainsオブジェクトを返す
3. :dataframes      # DataFrames.DataFrameオブジェクトを返す
4. :namedtuple      # NamedTupleオブジェクトを返す

最初のオプション（デフォルト）は、ndraws、nvars、nchainsをインデックスとするArray{Float64, 3}を返します。

2番目のオプションはMCMCChains.Chainsオブジェクトを返し、3番目はDataFrameオブジェクト、最後のオプションはNamedTupleを返します。
```

### 例

```julia
stanmodel = Stanmodel(num_samples=1200, thin=2, name="bernoulli", 
  model=bernoullimodel);
```

### 関連ヘルプ

```julia
?stan                                  : Stanmodelを実行
?CmdStan.Sample                        : サンプリング設定
?CmdStan.Method                        : 利用可能なメソッドのリスト
?CmdStan.Output                        : 出力ファイル設定
?CmdStan.DataDict                      : 入力データ
?CmdStan.convert_a3d                   : 出力形式のオプション
```
