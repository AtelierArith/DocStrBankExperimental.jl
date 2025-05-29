```
GridSagSurface{T,N,S<:Union{ZernikeSurface{T,N},ChebyshevSurface{T,N}},Nu,Nv} <: ParametricSurface{T,N}
```

グリッドサグ高さが基底サグに追加された、ゼルニケ（円形）またはチェビシェフ（長方形）サーフェスのいずれかです。サーフェスの形状は、`interpolation`引数によって設定されたサグ値の`Nu×Nv`グリッドの線形またはバイキュービックスプライン補間によって決まります。`interpolation`引数は`GridSagLinear`または`GridSagBicubic`のいずれかを取ります。

グリッドの各エントリは、$[z, \frac{\partial z}{\partial x}, \frac{\partial z}{\partial y}, \frac{\partial^2 z}{\partial x \partial y}]$の形式のベクトルです。最初のデータ項目はサーフェスの左下隅に対応し、すなわち、-uおよび-v制限によって定義されるコーナーです。その後の各点は、サーフェスの面を左から右に移動しながら上に読み取られます。部分導関数にゼロが与えられた場合（バイキュービック補間を使用している場合）、部分導関数は有限差分を使用して近似されます。

サググリッドはuv空間内のサーフェスからオフセットすることができ、その場合、サーフェスはグリッドが定義されている領域の外側で不安定になる可能性があります。この場合、CSG操作を使用して有効な領域にサーフェスをクリップすることをお勧めします。

サーフェスは、ファイル名を最初の唯一の位置引数として渡すことによって`.GRD`ファイルからも生成できます。この場合、サーフェスは長方形になり、オプションで半径と円錐が設定されます。

基底サーフェスの詳細については、[`ZernikeSurface`](@ref)および[`ChebyshevSurface`](@ref)のドキュメントを参照してください。

```julia
GridSagSurface(basesurface::Union{ZernikeSurface{T,N},ChebyshevSurface{T,N}}, sag_grid::AbstractArray{T,3}; interpolation = GridSagBicubic, decenteruv = (0, 0))
GridSagSurface{T}(filename::String; radius = Inf, conic = 0, interpolation = GridSagBicubic)
```
