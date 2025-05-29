`@usingmerge [reexport] [verbose=true] SomeModule[: symbol1, symbol2...]`

モジュール `SomeModule` を `using` し、さらに `SomeModule` によってエクスポートされたすべてのメソッド定義（または `SomeModule` からのメソッド定義 `symbol1, symbol2...`）を現在のモジュールの同名のメソッドとマージします。

`reexport` が指定されている場合、`SomeModule` からエクスポートされたすべての新しい名前（現在のモジュールの名前と衝突しないもの）は、現在のモジュールから（再）エクスポートされます。名前が新しくない場合、それをエクスポートするかどうかの決定は以前に行われたと見なされます。

`verbose=true` の場合、衝突するメソッドが印刷されます。`verbose=2` の場合、実行前に実行されるすべてのコマンドが印刷されます。`verbose=3` の場合、両方が発生します。

`SomeModule` によってエクスポートされた名前がメソッドでない名前と衝突する場合、警告が印刷され、その名前はマージされません（インポートされません）。

使用例:

```julia
julia> using UsingMerge

julia> foo(x::Int)=2
foo (generic function with 1 method)

julia> module Bar
       export foo
       foo(x::Float64)=3
       end
Main.Bar

julia> @usingmerge verbose=3 Bar
# Bar.foo conflicts with Main.foo --- adding methods
Main.foo(x::Float64) = Bar.foo(x)
```

`@usingmerge Bar: foo` を使用して `foo` のみをインポート/マージすることもできます。いずれにせよ、名前 `Bar` をスコープに入れるために、`using Bar: Bar` の同等の処理が行われることに注意してください。
