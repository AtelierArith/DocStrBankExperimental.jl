```
ShowCase(o, props=propertynames(o);
         type_style=Style(), show_module=:context,
         max_params=3, show_params=true, kw...)
```

`AbstractShow`オブジェクトを作成し、デフォルトの`show`メソッドで使用されるすべての要素を組み合わせます。これは[`ShowTypeOf`](@ref)と[`ShowProps`](@ref)を連結します。

## 引数

  * `o`: ラップされるオブジェクト。
  * `props`: 表示されるオブジェクトのプロパティ。
  * `type_style`: 型に使用されるスタイル。
  * `show_module::Symbol`: 型と型パラメータのモジュールを表示するかどうか、[`ShowType`](@ref)を参照してください。
  * `max_params::Integer`: 表示する型パラメータの最大数。
  * `show_params::Bool`: パラメータを表示するかどうか。`max_params=0`かつ`show_params=true`の場合、継続文字列を含む括弧が表示されることに注意してください。
  * `kw`: [`ShowProps`](@ref)に渡される他のキーワード引数。

## 例

```
julia> ShowCase(1.0 + im)
ComplexF64{Float64}(re=1.0, im=1.0)

julia> ShowCase(1.0 + im, new_lines=true)
ComplexF64{Float64}(
    re = 1.0,
    im = 1.0
)

julia> ShowCase(1.0 + im, type_style=Style(:cyan, true), max_params=0)
ComplexF64{…}(re=1.0, im=1.0)

julia> ShowCase(1.0 + im, [:im], keyword_style=Style(:magenta))
ComplexF64{Float64}(im=1.0)
```
