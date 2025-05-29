```
DEModel{F,L,T,S} <: AbstractModel where {F <: Function,L,T,S}
```

対数尤度関数と事前分布を含むモデルオブジェクト。

# フィールド

  * `prior_loglike::L`: 事後サンプルの対数尤度。`sample`のために関数が定義されている必要がありますが、`optimize`のためには必要ありません。
  * `loglike::F`: ベイズパラメータ推定のための対数尤度関数または最適化のための目的関数。
  * `sample_prior::S`: 初期値のための関数。通常、事前分布が理想的です。
  * `names::T`: パラメータ名

# コンストラクタ

```
function DEModel(
    args...; 
    prior_loglike = nothing, 
    loglike, 
    names, 
    sample_prior, 
    data, 
    kwargs...)
```

# 引数

  * `args...`: `loglike`のためのオプショナル位置引数

# キーワード

  * `prior_loglike=nothing`: 事後サンプルの対数尤度。`sample`のために関数が定義されている必要がありますが、`optimize`のためには必要ありません。
  * `loglike`: ベイズパラメータ推定のための対数尤度関数または最適化のための目的関数。
  * `sample_prior`: 初期値のための関数。通常、事前分布が理想的です。
  * `names`: パラメータ名
  * `kwargs...`: `loglike`のためのオプショナルキーワード引数
