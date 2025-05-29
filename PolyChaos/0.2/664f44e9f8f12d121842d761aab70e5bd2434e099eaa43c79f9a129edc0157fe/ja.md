**単変量**

```
sampleMeasure(n::Int,name::String,w::Function,dom::Tuple{<:Real,<:Real},symm::Bool,d::Dict;method::String="adaptiverejection")
sampleMeasure(n::Int,m::Measure;method::String="adaptiverejection")
sampleMeasure(n::Int,op::AbstractOrthoPoly;method::String="adaptiverejection")
```

測度 `m` から `n` サンプルを引き出します。これは以下によって説明されます。

  * `name`
  * 重み関数 `w`,
  * ドメイン `dom`,
  * 対称性の特性 `symm`,
  * そして、該当する場合は辞書 `d` に格納されたパラメータ。デフォルトでは、適応的拒否サンプリング法が使用されます（[AdaptiveRejectionSampling.jl](https://github.com/mauriciogtec/AdaptiveRejectionSampling.jl)から）、共通の確率変数の場合は [Distributions.jl](https://github.com/JuliaStats/Distributions.jl) が使用されます。

この関数は `AbstractOrthoPoly` を受け入れるようにディスパッチされます。

**多変量**

```
sampleMeasure(n::Int,m::ProductMeasure;method::Vector{String}=["adaptiverejection" for i=1:length(m.name)])
sampleMeasure(n::Int,mop::MultiOrthoPoly;method::Vector{String}=["adaptiverejection" for i=1:length(mop.meas.name)])
```

多変量拡張で、`n` 行のサンプルの配列を提供し、多重測度が持つ単変量測度の数だけ列があります。
