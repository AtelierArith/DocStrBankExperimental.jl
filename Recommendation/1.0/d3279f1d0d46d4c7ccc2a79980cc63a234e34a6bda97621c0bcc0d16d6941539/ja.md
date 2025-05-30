```
load_libsvm_file(path::String; zero_based::Bool=false, n_features::Union{Integer, Nothing}=nothing) -> X, y
```

[libsvm形式](https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/)で表現されたスパースマトリックスデータセットを読み込みます。Xとyの各行は、すでにベクトルに変換されたサンプルのペアに対応しています。データにはユーザー/アイテムIDの概念がないため、ユーザーは結果のマトリックス/ベクトルを手動で`DataAccessor`に変換する必要があります。

```julia
n_users, n_items = ...

X, y = load_libsvm_file("/path/to/data.libsvm")

events = Event[]
for i in 1:length(y)
    user, item = ... # 自分の定義に基づいて行ごとのユーザー/アイテムIDを見つける
    push!(events, Event(user, item, y[i]))

data = DataAccessor(events, n_users, n_items)

# Xのどの列がそれぞれユーザーとアイテムの特徴を表すかを宣言します
user_feature_indices = [...]
item_feature_indices = [...]

for i in 1:size(X, 1)
    user, item = ... # 自分の定義に基づいて行ごとのユーザー/アイテムIDを見つける
    set_user_attributes(data, user, X[i, user_feature_indices])
    set_item_attributes(data, item, X[i, item_feature_indices])
```
