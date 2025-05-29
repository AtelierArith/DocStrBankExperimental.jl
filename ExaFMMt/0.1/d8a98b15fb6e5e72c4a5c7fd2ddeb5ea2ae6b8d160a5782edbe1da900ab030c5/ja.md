```
ExaFMM{K} <: LinearMaps.LinearMap{K}
```

は、fmm行列に似た型であり、ソースポイントの電荷などのベクトルと掛け算することができます。この型は、C++部分の割り当てられたストレージを解放するためにガーベジコレクタに必要です。

# フィールド

  * `fmmoptions::FMMOptions`: LaplaceFMMOptions、HelmholtzFMMOptions、またはModifiedHelmholtzFMMOptionsのいずれかを初期化します。
  * `nsources::Int`: ソースの数。
  * `ntargets::Int`: ターゲットの数。
  * `fmm::Ptr{Cvoid}`: C++部分によって生成されたfmm構造体へのポインタ。
  * `fmmstruct::Ptr{Cvoid}`: fmmのすべての必要なサブ構造体を持つ構造体へのポインタ。このポインタはC++部分との通信に必須です。
  * `sources::Ptr{Cvoid}`: ソースのC++構造体へのポインタ。
  * `targets::Ptr{Cvoid}`: ターゲットのC++構造体へのポインタ。
