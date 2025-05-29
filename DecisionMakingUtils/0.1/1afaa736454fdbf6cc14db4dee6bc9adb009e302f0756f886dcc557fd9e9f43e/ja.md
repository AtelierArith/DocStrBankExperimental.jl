```
LinearNormalization{T}(a::T,b::T)
```

これはベクトル x を $(x - a) * b$ として正規化するファンクタです。これは、$[0,1]$、$[-1,1]$、および平均ゼロ標準偏差1へのマッピングなど、すべての線形正規化の標準インターフェースです。LinearNormalization は、関数 Base.lenght と Base.eltype もサポートしています。

参照: [`PosNegNormalization`](@ref), [`GaussianNormalization`](@ref)

# 例

```jldoctest
julia> nrm = LinearNormalization([0.1, 2.0], [1.0, 0.5]);

julia> x = [1.0, 2.0];

julia> nrm(x)
2-element Vector{Float64}:
 0.9
 0.0

julia> nrm = LinearNormalization(2);  # 入力ベクトルにスケーリングなし

julia> nrm(x)
2-element Vector{Float64}:
 1.0
 2.0

julia> low = [0.0, -1.0];

julia> high = [3.0, 0.5];

julia> nrm = ZeroOneNormalization(low, high);  # 各エントリを [0,1] に正規化

julia> x = [1.0, 0.0];

julia> feats = nrm(x)
2-element Array{Float64,1}:
0.3333333333333333
0.6666666666666666

julia> y = zero(x);  # アロケーションを防ぐためのバッファを作成

julia> feats = nrm(y, x);  # アロケーションなしで返す

julia> nrm = PosNegNormalization(low, high);  # 各エントリを [0,1] に正規化

julia> nrm(x)
2-element Vector{Float64}:
 -0.3333333333333333
  0.3333333333333333

julia> μ = [0.0, 1.0];  # 平均のベクトル

julia> σ = [1.0, 2.0];  # 標準偏差のベクトル

julia> nrm = GaussianNormalization(μ, σ);  # x を平均0、標準偏差1に正規化

julia> nrm(x)
2-element Vector{Float64}:
  1.0
 -0.5
```
