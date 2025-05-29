```
load_libsvm_file(path::String; zero_based::Bool=false, n_features::Union{Integer, Nothing}=nothing) -> X, y
```

Read a sparse matrix dataset represented by [libsvm format](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/). Each row of X and y corresponds to a pair of sample that is already transformed to a vector; since there is no concept of user/item ID in the data, users may need to manually translate the resulting matrix/vector to `DataAccessor` as:

```julia
n_users, n_items = ...

X, y = load_libsvm_file("/path/to/data.libsvm")

events = Event[]
for i in 1:length(y)
    user, item = ... # find user/item ID per row based on your definition
    push!(events, Event(user, item, y[i]))

data = DataAccessor(events, n_users, n_items)

# declare which columns in X represent user and item features, respectively
user_feature_indices = [...]
item_feature_indices = [...]

for i in 1:size(X, 1)
    user, item = ... # find user/item ID per row based on your definition
    set_user_attributes(data, user, X[i, user_feature_indices])
    set_item_attributes(data, item, X[i, item_feature_indices])
```
