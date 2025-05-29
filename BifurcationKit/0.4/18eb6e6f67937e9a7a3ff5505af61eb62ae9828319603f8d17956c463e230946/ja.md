```julia
get_normal_form(
    prob,
    br,
    id_bif;
    nev,
    verbose,
    lens,
    Teigvec,
    scaleζ,
    detailed,
    autodiff,
    ζs,
    ζs_ad,
    bls,
    bls_adjoint,
    bls_block
)

```

`br.specialpoint[ind_bif]`に位置する分岐点の正規形を計算します。

# 引数

  * `prob::AbstractBifurcationProblem`
  * `br` [`continuation`](@ref)の呼び出しからの結果
  * `ind_bif` `br.specialpoint`における分岐点のインデックス

# オプション引数

  * `nev` スペクトル射影を計算するために使用される固有値の数。この数は反復法で使用する際に調整する必要があります。
  * `verbose` 情報を表示するかどうか
  * `ζs` 分岐点での`dF`のカーネルを張るベクトルのリスト。正規形の基底を強制するのに便利です。
  * `lens::Lens` 偏微分∂pFを取るパラメータを指定します。
  * `scaleζ` カーネル基底を正規化するための関数。実際、大きなベクトルと`norm`を使用すると、ζsと正規形係数が非常に小さくなります。
  * `autodiff = true` 正規形を計算するために必要なパラメータに対する微分にForwardDiffを使用するかどうか。例えば、Bogdanov-Takens点に使用されます。希望する場合は`autodiff = false`に設定できます。
  * `detailed = true` 簡略化された正規形のみを計算するかどうか。例えば、Bogdanov-Takens点に使用されます。
  * `bls = MatrixBLS()` 境界付き線形ソルバーを指定します。例えば、Bogdanov-Takens点に使用されます。
  * `bls_adjoint = bls` 隣接問題のための境界付き線形ソルバーを指定します。
  * `bls_block = bls` 境界の次元が2（`bls`の場合は1）であるときの境界付き線形ソルバーを指定します。

# 利用可能なメソッド

```
get_normal_form(br, ind_bif ; kwargs...)
```

を直接呼び出すことができ、これは`get_normal_form(getprob(br), br, ind_bif ; kwargs...)`のショートカットです。

正規形`nf`が計算されたら、`predictor(nf, δp)`を呼び出して分岐する枝の推定を取得できます。
