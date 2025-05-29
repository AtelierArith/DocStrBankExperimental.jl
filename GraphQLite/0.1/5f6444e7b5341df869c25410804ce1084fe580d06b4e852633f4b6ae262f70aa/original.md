```
resolve(parent::T, field::Val{F}, args)
```

## Example:

```julia
function GraphQLite.resolve(parent::GQLQuery, field::Val{:getCart}, args)
    # return a object of type Cart
end
```
