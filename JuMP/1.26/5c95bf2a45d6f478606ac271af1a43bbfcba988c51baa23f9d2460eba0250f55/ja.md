```
optimizer_with_attributes(optimizer_constructor, attrs::Pair...)
```

最適化子コンストラクタを属性のリスト `attrs` とグループ化します。これは `MOI.OptimizerWithAttributes` と同等です。

`Model` コンストラクタや [`set_optimizer`](@ref) に提供されると、`optimizer_constructor()` を呼び出して最適化子を作成し、その後 [`set_attribute`](@ref) を使用して属性を設定します。

関連情報: [`set_attribute`](@ref), [`get_attribute`](@ref).

## 注意

属性の文字列名は各ソルバーに特有です。興味のある属性を見つけるためには、ソルバーのドキュメントを参照する必要があります。

## 例

```jldoctest
julia> import HiGHS

julia> optimizer = optimizer_with_attributes(
           HiGHS.Optimizer, "presolve" => "off", MOI.Silent() => true,
       );

julia> model = Model(optimizer);
```

は次のように等価です:

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_attribute(model, "presolve", "off")

julia> set_attribute(model, MOI.Silent(), true)
```
