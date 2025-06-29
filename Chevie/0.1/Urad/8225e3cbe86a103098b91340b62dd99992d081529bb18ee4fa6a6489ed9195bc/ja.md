`struct UnipotentGroup` は、冗長群 `G` のボレル部分群のユニポテント根 `𝐔` を表します。

以下の詳細については、[Carter1972, section 4.2](biblio.htm#Car72b) を参照してください。`𝐔` のリー代数のシェバレ基底は、各 `eᵣ` が対応する根部分空間にある基底 `eᵣ` であり、`[eᵣ,eₛ]=Nᵣₛ e_{r+s}` となるような整数定数 `Nᵣₛ` が存在します。一般の根に対する定数 `Nᵣₛ` は、`r` と `s` が根の和が根である正の根である場合のケースから計算されます。そのような対 `(r,s)` は *特別* と呼ばれます。

定数 `Cᵣₛᵢⱼ` は、[Carter1972, 5.2.3](biblio.htm#Car72b) で定義されており、次のように表されます。

$$
u_s(u)u_r(t)=u_r(t)u_s(u)\prod_{i,j>0}u_{ir+js}(C_{rsij}(-t)^iu^j)
$$

ここで、`ir+js` は、根である `r` と `s` の正の整数の組み合わせを、`(i,j)` の辞書順で取ります。定数 `Cᵣₛᵢⱼ` は、定数 `Nᵣₛ` から計算されます。詳細は、[Carter1972, ページ61の下部およびページ76の上部](biblio.htm#Car72b) を参照してください。

`struct UnipotentGroup` のフィールドは次のとおりです：

  * `W`:         `G` のワイル群
  * `order`:     根の正規化に使用される根部分群の総順序（デフォルトは `1:nref(W)`）
  * `special`:   各特別な根の対 `(r,s)` のための `NamedTuple`
  * `r`:        `r` のインデックス
  * `s`:        `s` のインデックス
  * `rs`:       `r+s` のインデックス
  * `N`:        定数 `Nᵣₛ`
  * `comm`:     四重項のリスト `(i,j,ir+js,Cᵣₛᵢⱼ)` として `Cᵣₛᵢⱼ` を格納します。

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2))
UnipotentGroup(G₂)

julia> U.special
10-element Vector{@NamedTuple{r::Int64, s::Int64, rs::Int64, N::Int64, comm::Vector{NTuple{4, Int64}}}}:
 (r = 1, s = 2, rs = 3, N = 1, comm = [(1, 1, 3, 1), (1, 2, 4, -1), (1, 3, 5, 1), (2, 3, 6, 2)])
 (r = 2, s = 3, rs = 4, N = 2, comm = [(1, 1, 4, 2), (2, 1, 5, 3), (1, 2, 6, -3)])
 (r = 2, s = 4, rs = 5, N = 3, comm = [(1, 1, 5, 3)])
 (r = 1, s = 5, rs = 6, N = 1, comm = [(1, 1, 6, 1)])
 (r = 3, s = 4, rs = 6, N = 3, comm = [(1, 1, 6, 3)])
 (r = 2, s = 1, rs = 3, N = -1, comm = [(1, 1, 3, -1), (2, 1, 4, -1), (3, 1, 5, -1), (3, 2, 6, -1)])
 (r = 3, s = 2, rs = 4, N = -2, comm = [(1, 1, 4, -2), (2, 1, 6, -3), (1, 2, 5, 3)])
 (r = 4, s = 2, rs = 5, N = -3, comm = [(1, 1, 5, -3)])
 (r = 5, s = 1, rs = 6, N = -1, comm = [(1, 1, 6, -1)])
 (r = 4, s = 3, rs = 6, N = -3, comm = [(1, 1, 6, -3)])
```
