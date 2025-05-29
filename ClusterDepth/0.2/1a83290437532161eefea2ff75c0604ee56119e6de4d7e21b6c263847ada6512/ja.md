using Base: Stateful clusterdepth(rng,data::AbstractArray;τ=2.3, statfun=x->abs.(studentt(x)),permfun=sign*permute!,nperm=5000,pval*type=:troendle)

与えられたデータマトリックスのクラスタ深度を計算します。

  * `data`: `statfun` はデータの最後の次元に適用されます（通常、これは被験者になります）

オプション

  * `τ`: クラスタ形成の閾値
  * `nperm`: 繰り返しの数、デフォルトは5000
  * `stat_type`: デフォルトは一標本の `t-test`、カスタム関数を指定できます（`statfun!` と `statfun` を参照）
  * `side_type`: デフォルト: `:abs` - `statfun` の後に適用される関数は何ですか？ `:abs`、`:square`、正のクラスタをテストするための `:positive`、負のクラスタをテストするための `:negative` などが考えられます。カスタム関数を提供できます（`sidefun` を参照）
  * `perm_type`: デフォルト `:sign` は一標本データ（例：差分）に対して、符号反転を行います。カスタム関数を提供できます（`permfun` を参照）
  * `pval_type`: 各クラスタ内でp値を計算する方法、デフォルト `:troendle`、`?pvals` を参照
  * `statfun` / `statfun!` は、1つまたは2つの引数を取り、最後の次元で集約する関数です。2つの引数の場合、最初の引数がインプレースで変更され、適切なベクトル/マトリックスを提供することを期待します。
  * `sidefun`: デフォルト `abs`。`statfun` の出力の各要素に適用される関数を提供します。
  * `permfun` データを置換する関数で、RNGオブジェクトとデータを受け入れる必要があります。インプレースで行うことができ、データはコピーされますが、同じ配列が置換間で共有されます。
