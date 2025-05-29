```
ref(p::Union{ArbPoly,ArbSeries,AcbPoly,AcbSeries}, i)
```

`p[i]`と似ていますが、`Arb`または`Acb`の代わりに`p`のi番目の係数とメモリを共有する`ArbRef`または`AcbRef`を返します。

!!! note
    係数を読み取るために`ref`を使用することは常に安全ですが、係数が変更される場合は注意が必要です。変更を処理する方法については、下のコメントを参照してください。


これは、割り当てられた係数にのみアクセスを許可します。`ArbPoly`および`AcbPoly`の場合、これは通常、ポリノミアルの次数までのすべての係数ですが、例えば`Arblib.fit_length!`が使用されると、より高くなる可能性があります。`ArbSeries`および`AcbSeries`の場合、基になるポリノミアルの次数が低くても、次数までのすべての係数が割り当てられていることが保証されています。

係数がポリノミアルの次数を変更する方法で変更された場合、ポリノミアルの内部に保存された長さも更新する必要があります。

  * 新しい次数が同じか低い場合、次のようにして達成できます。

    ```
    Arblib.normalise!(p)
    ```
  * 新しい次数が高い場合は、長さを手動で設定する必要があります。これは次のようにして達成できます。

    ```
    Arblib.set_length!(p, len)
    Arblib.normalise!(p)
    ```

    ここで`len`は新しい次数の上限よりも1つ高い値です。

詳細については、拡張ヘルプを参照してください。

# 拡張ヘルプ

ここでは、先頭係数が変更されて次数が下がる例を示します。

```jldoctest
julia> p = ArbPoly([1, 2], prec = 64) # 次数1の多項式
1.0 + 2.0⋅x

julia> Arblib.zero!(Arblib.ref(p, 1)) # 先頭係数を0に設定
0

julia> Arblib.degree(p) # 次数はまだ1として報告される
1

julia> length(p) # 長さは2として報告される
2

julia> p # 印刷すると奇妙な結果が得られる
1.0 +

julia> Arblib.normalise!(p) # 多項式を正規化すると次数が更新される
1.0

julia> Arblib.degree(p) # これは正しい
0

julia> p # 印刷も正しい
1.0
```

次数を超える係数が変更される例を示します。

```jldoctest
julia> q = ArbSeries([1, 2, 0], prec = 64) # 先頭係数がゼロの次数3の系列
1.0 + 2.0⋅x + 𝒪(x^3)

julia> Arblib.one!(Arblib.ref(q, 2)) # 先頭係数を1に設定
1.0

julia> q # 先頭係数は認識されない
1.0 + 2.0⋅x + 𝒪(x^3)

julia> Arblib.degree(q.poly) # 基になる多項式の次数はまだ1
1

julia> Arblib.set_length!(q, 3) # 長さを明示的に3に設定した後は問題ない
1.0 + 2.0⋅x + 1.0⋅x^2 + 𝒪(x^3)
```
