4次元の場合の第二チェルン数をFukui-Hatsugai-Suzuki法に基づいて計算します [Fukui2005Chern,Mochol-Grzelak2018Efficient](@cite)。

```
calcSecondChern(Hamiltonian::Function; Nfill::T1=nothing, N::T2=(30, 30, 30, 30), returnRealValue::Bool=true, parallel::T3=UseSingleThread()) where {T1<:Union{Int,Nothing},T2<:Union{AbstractVector,Tuple},T3<:TopologicalNumbersParallel}
```

引数

  * `Hamiltionian`: 引数として2次元波数`k`を持つハミルトニアン行列。
  * `Nfill::T1`: フィリング数。デフォルト値は`Hs ÷ 2`で、`Hs`はハミルトニアン行列のサイズです。
  * `N::T2`: ブリルアンゾーンを離散化する際のメッシュ数。`N`の各要素は、x、y、z、およびw方向のメッシュ数です。
  * `returnRealValue::Bool`: トポロジカル数の値を実数値で返すオプション。`true`の場合、トポロジカル数は`Float64`型の値を返し、`false`の場合は`ComplexF64`型の値を返します。

# 例
