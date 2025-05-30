```
add!(mesh1, mesh2; kwargs...)
```

既存のメッシュにオプションのプロパティをキーワードとしてキャプチャしながらメッシュを手動で追加します。プロパティが一貫していることを確認してください（両方のメッシュは同じプロパティのリストを持つ必要があります）。たとえば、シーンが`:colors`で作成された場合、新しいメッシュにも`:colors`を提供する必要があります。

# 引数

  * `mesh1`: 拡張したい現在のメッシュ。
  * `mesh2`: 追加したい新しいメッシュ。
  * `kwargs`: 新しいメッシュの各三角形に設定するプロパティ。

# 例

```jldoctest
julia> t1 = Triangle(length = 1.0, width = 1.0);

julia> using ColorTypes: RGB

julia> add_property!(t1, :colors, rand(RGB));

julia> t2 = Rectangle(length = 5.0, width = 0.5);

julia> add!(t1, t2, colors = rand(RGB));
```
