```
checkmode(m, s::Symbol)
checkmode(m, [&, |, ==, or !], s₁::Symbol[, s₂:Symbol]...)
checkmode(f, m, [&, |, ==, or !], s₁::Symbol[, s₂:Symbol]...)
```

`m`が`Mode`であり、指定されたシンボルを含んでいるかどうかをテストします。

  * 1番目の形式では、関数は`m`に`s`が存在するかどうかをテストします。
  * 2番目の形式では、関数は（`&`の場合、または任意の演算子シンボルが省略された場合）すべてのシンボル`s₁`、`s₂`、...が`m`に含まれているか、または（`|`の場合）それらのうち少なくとも1つが`m`に含まれているか、または（`==`の場合）`m`が正確に指定されたシンボルのコレクションを含んでいるか、または（`!`の場合）`m`が指定されたシンボルのいずれも含んでいないかをテストします。
  * 3番目の形式では、関数はすべてのシンボル`s₁`、`s₂`、...が`m`に含まれているかどうかをテストします（`&`が提供されている場合も同様です）。含まれている場合は`f(m[s₁], m[s₂],  ...)`を返します。含まれていない場合は`nothing`を返します。`==`も関数呼び出しに追加されている場合、テストは`m`がすべての指定されたシンボルを含み、かつそれだけを含むときのみ陽性になります。`!`が関数呼び出しに追加されている場合、テストは`m`が指定されたシンボルのいずれも含まないときのみ陽性になります；その場合、`f`は引数なしで呼び出されます。同様に`|`の場合も、テストが真であれば、`f`は引数なしで呼び出されます。

参照: [`ArgumentModes.Mode`](@ref)

# 例

```julia-repl
julia> m = Mode(:a => 1, :b => 2.5, :c)
Mode[==, :b => Float64, :a => Int64, :c]((a = 1, b = 2.5, c = nothing))

julia> checkmode(m, :a)
true

julia> checkmode(m, :d)
false

julia> checkmode(m, |, :a, :d)
true

julia> checkmode(m, &, :a, :d)
false

julia> checkmode(m, ==, :a, :b)
false

julia> checkmode(m, ==, :a, :b, :c)
true

julia> checkmode(m, :a) do a;  @show a   end
a = 1
1

julia> checkmode(m, :a, :b) do a, b;  @show a, b   end
(a, b) = (1, 2.5)
(1, 2.5)

julia> checkmode(m, :a, :e) do x, y;  @show x, y   end

julia> checkmode(12, :a)
false
```
