ANND*in(A::T, vs=1:size(A,1); check*dimensions::Bool=true, check_directed::Bool=true) where {T<:AbstractMatrix}

隣接行列 `A` を持つグラフ内のすべてのノードに対する平均最近接隣人の入次数 (ANND) に対応するベクトルを返します。もし v が指定されている場合、v のノードに対する ANND_in のみを返します。

関連情報: [`ANND_out`](@ref), [`ANND`](@ref)
