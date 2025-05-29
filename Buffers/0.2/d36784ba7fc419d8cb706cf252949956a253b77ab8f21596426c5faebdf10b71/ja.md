```
neuralyze(tensor::AbstractArray)
```

`tensor`の起源に関するメモリを消去します。

`tensor`は（連続した！）配列であり、より大きな配列の（おそらく再形成された）ビューです。起源に関する情報なしで、同じメモリを指す同じテンソルを返します。`Base.mightalias`を欺くために、[`alloc!`](@ref)または[`reshape_buf!`](@ref)と一緒に使用されるべきです。

!!! warning
    この関数は安全ではなく、注意して使用する必要があります！メモリを消去しすぎると、Juliaが元の配列をガーベジコレクトし、テンソルが無効なメモリを指すことになります。また、バッファサイズが変更される可能性がある場合は、この関数を使用しないでください。


!!! tip
    `GC.@preserve`を使用して元の配列のガーベジコレクションを防ぐことができます（ただし、これは必要ないはずです）。


# 例

```julia
julia> buf = Buffer(100000)
julia> A = alloc(buf, 10, 10, 20) # 10x10x20 テンソル
julia> B = alloc(buf, 10, 10, 10) # Aの後に始まる10x10x10 テンソル
julia> C = alloc(buf, 10, 20) # Bの後に始まる10x20 テンソル
julia> rand!(B)
julia> rand!(C)
julia> An = neuralyze(A) # 起源なしで同じメモリを指すテンソル
julia> @tensor An[i,j,k] = B[i,j,l] * C[l,k]
```
