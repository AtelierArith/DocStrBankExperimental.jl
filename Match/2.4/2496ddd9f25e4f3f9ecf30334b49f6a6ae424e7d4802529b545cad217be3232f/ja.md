```
@match pattern = value
@match value begin
    pattern1 => result1
    pattern2 => result2
    ...
end
```

与えられた値をパターンまたは一連のパターンに一致させます。

このマクロには2つの形式があります。最初の形式は

```
@match pattern = value
```

パターンに一致する場合は値を返し、任意のパターン変数をバインドします。そうでない場合は `MatchFailure` をスローします。

2番目の形式は

```
@match value begin
    pattern1 => result1
    pattern2 => result2
    ...
end
```

最初に一致する `pattern` に対して `result` を返します。一致するものがない場合は `MatchFailure` をスローします。

`MatchFailure` 例外を避けるために、すべての可能な入力を処理するように `@match` を記述してください。その方法の1つは、ワイルドカードパターン `_` を持つ最終ケースを追加することです。

# 参照

参照してください

  * `@match_fail`
  * `@match_return`
  * `@ismatch`

# パターン:

次の構文形式をパターンで使用できます。

  * `_` は任意の値に一致します
  * `x` (識別子) は任意の値に一致し、それを変数 `x` にバインドします
  * `T(x,y,z)` は、フィールドがパターン `x,y,z` に一致する型 `T` の構造体に一致します
  * `T(y=p)` は、`y` フィールドがパターン `p` に一致する型 `T` の構造体に一致します
  * `(;x,y,z)` は、フィールド `x,y,z` が変数 `x,y,z` にバインドされる値に一致します
  * `(;x=p)` は、フィールド `x` がパターン `p` に一致する値に一致します; `x` はバインドされません。
  * `(;x::T)` は、フィールド `x` がパターン `::T` に一致する値に一致します; また、フィールドを `x` にバインドします
  * `[x,y,z]` は、3つのエントリが `x,y,z` に一致する `AbstractArray` に一致します
  * `(x,y,z)` は、3つのエントリが `x,y,z` に一致する `Tuple` に一致します
  * `[x,y...,z]` は、少なくとも2つのエントリを持つ `AbstractArray` に一致し、`x` が最初のエントリに一致し、`z` が最後のエントリに一致し、`y` が残りのエントリに一致します。
  * `(x,y...,z)` は、少なくとも2つのエントリを持つ `Tuple` に一致し、`x` が最初のエントリに一致し、`z` が最後のエントリに一致し、`y` が残りのエントリに一致します。
  * `::T` は型 `T` の任意のサブタイプ (`isa`) に一致します
  * `x::T` は、パターン `x` にも一致する型 `T` の任意のサブタイプ (`isa`) に一致します
  * `x || y` は、パターン `x` または `y` のいずれかに一致する値に一致します (両方のブランチに存在する変数のみがバインドされます)
  * `x && y` は、両方のパターン `x` と `y` に一致する値に一致します
  * `x, if condition end` は、`condition` が真である場合のみ一致します (`condition` は、パターン内で以前に発生した任意の変数を使用できます。例: `(x, y, z where x + y > z)`)
  * `x where condition` は `x, if condition end` の代替形式です
  * `if condition end` は、計算されたブールパターンです。 `x && if condition end` は `x where condition` の別の書き方です。
  * `1` (リテラル値) は、`isequal` を使用してその値に一致します
  * `r"[a-z]*"` (正規表現) は、正規表現に一致する文字列に一致します
  * `1:10` (定数範囲) は、その範囲内の値に一致します
  * 式は、標準の補間構文 `$(x)` を介して定数として補間できます。 補間は、以前にバインドされた変数を使用できます。

パターンは任意にネストできます。

繰り返し変数は、等しい場合にのみ一致します (`isequal`)。たとえば、`(x,x)` は `(1,1)` に一致しますが、`(1,2)` には一致しません。

# 例

```julia-repl
julia> value=(1, 2, 3, 4)
(1, 2, 3, 4)

julia> @match (x, y..., z) = value
(1, 2, 3, 4)

julia> x
1

julia> y
(2, 3)

julia> z
4

julia> struct Foo
           x::Int64
           y::String
       end

julia> f(x) = @match x begin
           _::String => :string
           [a,a,a] => (:all_the_same, a)
           [a,bs...,c] => (:at_least_2, a, bs, c)
           Foo(x, "foo") where x > 1 => :foo
       end
f (generic function with 1 method)

julia> f("foo")
:string

julia> f([1,1,1])
(:all_the_same, 1)

julia> f([1,1])
(:at_least_2, 1, Int64[], 1)

julia> f([1,2,3,4])
(:at_least_2, 1, [2, 3], 4)

julia> f([1])
ERROR: MatchFailure([1])
...

julia> f(Foo(2, "foo"))
:foo

julia> f(Foo(0, "foo"))
ERROR: MatchFailure(Foo(0, "foo"))
...

julia> f(Foo(2, "not a foo"))
ERROR: MatchFailure(Foo(2, "not a foo"))
...
```
