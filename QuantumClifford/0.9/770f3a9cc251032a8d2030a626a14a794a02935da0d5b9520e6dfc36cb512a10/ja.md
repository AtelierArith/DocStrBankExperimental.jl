多量子ビットパウリ演算子 ($±\{1,i\}\{I,Z,X,Y\}^{\otimes n}$)。

パウリは、`P`カスタム文字列マクロを使用して構築するか、より小さな演算子の積とテンソル積を通じて構築できます。

```jldoctest
julia> pauli3 = P"-iXYZ"
-iXYZ

julia> pauli4 = 1im * pauli3 ⊗ X
+ XYZX

julia> Z*X
+iY
```

内部的には、典型的なF(2,2)エンコーディングを使用しています。XビットとZビットは、ビット配列のUIntチャンクの単一の連結パディング配列に格納されています。

```jldoctest
julia> p = P"-IZXY";


julia> p.xz
2-element Vector{UInt64}:
 0x000000000000000c
 0x000000000000000a
```

XビットとZビットには、ゲッターとセッター、または`xview`、`zview`、`xbit`、`zbit`関数を通じてアクセスできます。

```jldoctest
julia> p = P"XYZ"; p[1]
(true, false)

julia> p[1] = (true, true); p
+ YYZ
```
