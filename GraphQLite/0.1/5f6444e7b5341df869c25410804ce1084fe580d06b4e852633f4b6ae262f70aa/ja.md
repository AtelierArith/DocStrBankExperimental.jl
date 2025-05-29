```
resolve(parent::T, field::Val{F}, args)
```

## 例:

```julia
function GraphQLite.resolve(parent::GQLQuery, field::Val{:getCart}, args)
    # Cart型のオブジェクトを返す
end
```
