このパッケージは、GAP構文を使用して有限体を導入します。GAPとの互換性が、このパッケージが既存の`GaloisFields`を使用しない理由です。速度は`GaloisFields`と同等で、素数体に対してはわずかに遅く、合成体に対しては速くなります。GAP3のように、私たちは2^16未満の次数の体のみを実装しています。このパッケージには、モジュラスに制限のないモジュラー算術を実装する`Modulo`モジュールが付属しています（モジュラスは`BigInt`であることができます）。

このパッケージの唯一の依存関係は`Primes`です。

`p^n`要素を持つガロア体は`GF(p^n)`として得られます。特性`p`のガロア体のすべての要素は同じ型を持ち、パラメトリック型は`FFE{p}`です。関数`Z(p^n)`は`GF(p^n)`の乗法群の生成元を返します。`GF(p^n)`の他の要素は`Z(p^n)`の累乗として得られ、`0`は`0*Z(p^n)`として得られます。素数体の要素も`FFE{p}(n)`として得ることができます（これは`n*Z(p)^0`と同じです）。

```julia-repl
julia> a=Z(64)
FFE{2}: Z₆₄

julia> a^9 # 自動的に小さい体に変換
FFE{2}: Z₈

julia> a^21
FFE{2}: Z₄

julia> a+1
FFE{2}: Z₆₄⁵⁶
```

素数体の要素は`Mod(,p)`または整数に変換できます：

```julia-repl
julia> a=Z(19)+3
FFE{19}: 5

julia> Mod(a)
Mod{UInt64}: 5₁₉

julia> Int(a)
5

julia> order(a) # 乗法群の要素としての順序
9
```

体、`p`、`n`および`p^n`は`FFE{p}`から取得でき、どの`Z(p^n)`の累乗が考慮されているかもわかります。

```julia-repl
julia> a=Z(8)^5
FFE{2}: Z₈⁵

julia> F=field(a)
GF(2^3)

julia> char(F)
2

julia> char(a)
2

julia> degree(F)
3

julia> degree(a)
3

julia> length(F)
8

julia> log(a)
5

julia> elements(F)
8-element Vector{FFE{2}}:
   0
   1
  Z₈
 Z₈²
 Z₈³
 Z₈⁴
 Z₈⁵
 Z₈⁶
```

`p`-整数または有理数、または`Mod(,p)`は、コンストラクタとして`FFE{p}`を使用して素数体の要素に変換できます。

```julia-repl
julia> FFE{19}(2)
FFE{19}: 2

julia> FFE{19}(5//3)
FFE{19}: 8

julia> FFE{19}(Mod(2,19))
FFE{19}: 2
```

```julia-rep1
julia> m=rand(GF(49),4,4)
4×4 Matrix{FFE{7}}:
 Z₄₉²⁴  Z₄₉¹⁸   Z₄₉⁹  Z₄₉⁴²
 Z₄₉²²  Z₄₉⁴¹  Z₄₉⁴⁶  Z₄₉²⁴
 Z₄₉¹⁵  Z₄₉¹⁹  Z₄₉⁴⁰   Z₄₉³
 Z₄₉²⁰  Z₄₉²⁹  Z₄₉³⁶  Z₄₉²⁰

julia> inv(m)
4×4 Matrix{FFE{7}}:
 Z₄₉³⁷   Z₄₉⁵  Z₄₉³⁶      1
 Z₄₉¹⁰    Z₄₉   Z₄₉⁶  Z₄₉⁴⁷
 Z₄₉³⁰  Z₄₉³⁸    Z₄₉     -2
 Z₄₉¹⁵   Z₄₉²      1  Z₄₉²⁸

julia> inv(m)*m
4×4 Matrix{FFE{7}}:
 1  0  0  0
 0  1  0  0
 0  0  1  0
 0  0  0  1
```
