```
function render
```

抽象関数。プラグインによって特化される必要があります。これは自動的に `Stipple` によって呼び出され、Juliaデータ型（`ReactiveModel` インスタンスのフィールドに対応）をJavaScript/JSONにシリアライズします。一般的に、特化されたメソッドはJuliaの `Dict` を返すべきであり、これは自動的に `Stipple` によってJSONエンコードされます。結果の `Dict` 内の特定の型に対してカスタムJSONシリアライゼーションが必要な場合は、その特定の型に対して `JSON.lower` を特化してください。

### 例

```julia
function Stipple.render(ps::PlotSeries, fieldname::Union{Symbol,Nothing} = nothing)
  Dict(:name => ps.name, ps.plotdata.key => ps.plotdata.data)
end
```

#### `Undefined` のための特化されたJSONレンダリング

```julia
JSON.lower(x::Undefined) = "__undefined__"
```
