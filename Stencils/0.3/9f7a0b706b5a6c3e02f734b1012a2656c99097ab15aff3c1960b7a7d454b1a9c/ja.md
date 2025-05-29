```
NamedStencil <: AbstractStencil

NamedStencil(; kw...)
NamedStencil(values::NamedTuple)
NamedStencil{Keys}(values)
```

名前付きステンシルで、各オフセット位置に名前を付けることができる任意の形状を取ることができます。これにより、マジックナンバーを取り除くことでステンシルコードが読みやすくなります。

## 例

```jldoctest
julia> using Stencils

julia> ns = NamedStencil(; west=(0, -1), north=(1, 0), south=(-1, 0), east=(0, 1)) 
NamedStencil{(:west, :north, :south, :east), ((0, -1), (1, 0), (-1, 0), (0, 1)), 1, 2, 4, Nothing}
▄▀▄
 ▀ 

julia> A = StencilArray((1:10) * (1:10)', ns);

julia> stencil(A, (5, 5)).east # 名前で値にアクセスできます
30

julia> mapstencil(s -> s.east + s.west, A); # そして `mapstencil` 関数で使用できます
```

既存のステンシルに名前を付けるショートカットも取ることができます：

```julia
julia> ns = NamedStencil{(:w,:n,:s,:e)}(VonNeumann(1)) 
```

ステンシルの半径は最も遠い座標から計算され、ステンシルの次元 `N` は最初の座標の長さから取得されます。例えば、`1`、`2`、または `3` です。
