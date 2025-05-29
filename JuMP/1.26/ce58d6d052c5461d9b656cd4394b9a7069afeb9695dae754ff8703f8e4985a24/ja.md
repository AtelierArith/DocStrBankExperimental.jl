```
show_backend_summary(io::IO, model::GenericModel)
```

モデルを支える最適化器の概要を表示します。

## 拡張

`AbstractModel` はこのメソッドを実装する必要があります。

## 例

```jldoctest
julia> model = Model();

julia> show_backend_summary(stdout, model)
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
