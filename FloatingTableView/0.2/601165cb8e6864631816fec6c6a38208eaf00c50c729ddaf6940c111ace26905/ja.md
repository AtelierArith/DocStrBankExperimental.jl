```
browse(t; newwindow = false, kwargs...)
```

Tables.jlの`showtable`関数を使用して、新しいBlinkウィンドウでデータソースをブラウズします。

# 引数

  * `t`、Tables.jl互換のデータソース、例えば`DataFrame`や`Vector`の`NamedTuple`
  * `newwindow`、データを上書きするのではなく新しい`Blink`ウィンドウで表示するためのブール型キーワード引数。新しいウィンドウでの表示は上書きよりも遅くなります。
  * `kwargs...`、新しいデータビューワーの詳細を制御するためにTableView.jlから`showtable`コマンドに渡されるキーワード引数。詳細については[`showtable`](@ref)を参照してください。

# 例

```julia
julia> t = (a = rand(10), b = rand(10))

julia> browse(t)
```

```julia
julia> t = rand(100, 100)

julia> browse(t, dark = true)
```

関連情報: [`showtable`](@ref) ```
