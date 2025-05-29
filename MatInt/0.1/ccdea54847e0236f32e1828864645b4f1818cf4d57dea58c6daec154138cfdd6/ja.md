`diaconis_graham(m::Matrix{<:Integer}, moduli::Vector{<:Integer})`

は、`moduli` によって定義されたアーベル群の生成子の集合に対して定義された標準形を返します。P. Diaconis と R. Graham の "The graph of generating sets of an abelian group", Colloq. Math., 80:31–38, 1999 に記載されています。

`moduli` は正のエントリを持ち、すべての `i` に対して `moduli[i+1]` が `moduli[i]` を割り切る必要があります。これはアーベル群 `A=ℤ/moduli[1]×…×ℤ/moduli[n]` を表し、ここで `n=length(moduli)` です。

`m` は `n` 列を持ち、各行は `i` 番目の要素が `mod moduli[i]` で取られ、`A` の要素を表します。`m` の行の集合は `A` を生成する必要があります。

関数は、`m` の行が `A` を生成しない場合は 'nothing' を返します。そうでない場合、フィールドを持つ名前付きタプル `r` を返します。

`r.normal`: Diaconis-Graham 標準形で、`m` と同じ形状の行列であり、最初の `n` 行が単位行列で、残りの行が `0` であるか、`length(m)=n` であり、`.normal` が単位行列と異なるのはエントリ `.normal[n,n]` のみで、これは `moduli[n]` に対して素です。

`r.rowtrans`: `r.normal==mod.(r.rowtrans*m,moduli')` となるようなユニモジュラー行列です。

以下は例です：

```julia-repl
julia> r=diaconis_graham([3 0;4 1],[10,5])
(rowtrans = [-13 10; 4 -3], normal = [1 0; 0 2])

julia> r.normal==mod.(r.rowtrans*[3 0;4 1],[10,5]')
true
```
