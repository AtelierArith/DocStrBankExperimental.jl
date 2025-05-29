```
delete(nms::Union{String, Vector{String}}; inall=ASKING, force = ASKING) -> nothing
delete(nm::AbstractString; inall=ASKING, force = ASKING) -> nothing
delete(p::Pair{<:AbstractString, <:AbstractString}; force = ASKING) -> nothing
```

共有環境またはその中のパッケージを削除します。

提供された引数が共有環境の名前（名前の先頭に「@」が付いている場合）である場合、共有環境のディレクトリを消去することによって共有環境を削除します。

そうでない場合、提供された名前はパッケージ名と見なされます。各パッケージ `pkg` に対して、共有環境から削除します。その後、パッケージ削除後に空になった場合は環境を削除します。

環境とパッケージの両方を `"@Foo" => "bar"` の形式で指定することもできます。

# キーワード引数

両方のキーワード引数は、Boolを含む任意の整数型や、整数値[-1=>SKIPPING, 0=>ASKING, 1=>FORCING]を持つ列挙型[`SkipAskForceEnum`](@ref)を受け入れます。Boolが使用される場合、`false`は`ASKING`に相当し、`true`は`FORCING`に相当します。

  * `inall=ASKING`: `FORCING`に設定すると、複数の環境からパッケージを削除しますが、`SKIPPING`の場合は尋ねずにスキップします。提供された`nms`が環境名である場合は影響を与えません。
  * `force=ASKING`: `FORCING`に設定すると、環境が現在`LOAD_PATH`にある場合でも環境を削除し、読み込まれている場合でもパッケージを削除します。

# 例

```julia-repl
julia> ShareAdd.delete("@TrialPackages")
julia> ShareAdd.delete(["UnusedPkg", "UselessPkg"]; inall=true)
julia> ShareAdd.delete("@Foo" => "bar")
```

この関数は公開されており、エクスポートされていません。
