```
getting(f) :: Lens
```

呼び出し可能な `f`（通常は型コンストラクタ）を適用してから値を取得します。すなわち、

```
get(obj, lens ∘ getting(f)) == f(get(obj, lens))
```

これは、例えば、タプルを `StaticVector` として取得し、設定時に再びタプルに変換するのに便利です。

`getting` は `f` と "フィールド" に格納されている値にいくつかの特性を要求することに注意してください。詳細は以下を参照してください。

# 例

```jldoctest
julia> using Kaleido, Setfield, StaticArrays

julia> obj = (x = ((0, 1, 2), "A"), y = "B");

julia> lens = (@lens _.x[1]) ∘ getting(SVector)
(@lens _.x[1]) ∘ (←|SVector{S, T} where {S, T}→)

julia> get(obj, lens) === SVector(obj.x[1])
true

julia> set(obj, lens, SVector(3, 4, 5))
(x = ((3, 4, 5), "A"), y = "B")
```

```jldoctest; filter = r"#[0-9]+"
julia> using Kaleido, Setfield, StaticArrays

julia> obj = (x = ((a = 0, b = 1, c = 2), "A"), y = "B");

julia> lens = (@lens _.x[1]) ∘ getting(Base.splat(SVector))
(@lens _.x[1]) ∘ (←|#60→)

julia> get(obj, lens) === SVector(obj.x[1]...)
true

julia> set(obj, lens, SVector(3, 4, 5))
(x = ((a = 3, b = 4, c = 5), "A"), y = "B")
```

# 詳細

`getting(f)` によって作成されたレンズは、以下に依存します：

  * 出力値 `y = f(x)` は、元の値 `x` に `C(y)` によって戻すことができる。ここで `C` は `x` のコンストラクタです。すなわち、このレンズを通じてオブジェクトから取得できる任意の `x` に対して、

    ```
    C(f(x)) == x
    ```
  * 逆方向の変換も成り立ちます。すなわち、このレンズを通じてオブジェクトに格納できる任意の `y` に対して、

    ```
    f(C(y)) == y
    ```

コンストラクタ `C` は、`x` のカスタム型のために `Setfield.constructor_of` を定義することで制御できます。
