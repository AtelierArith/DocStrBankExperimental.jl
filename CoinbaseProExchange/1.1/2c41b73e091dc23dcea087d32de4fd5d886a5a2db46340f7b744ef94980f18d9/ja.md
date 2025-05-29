```
show_all_accounts(user_data::UserInfo, currencies::Vector{String})
```

与えられたAPIキーに関連付けられたすべての暗号通貨アカウントの概要を取得します。

# 引数

  * `user_data::UserInfo` : APIデータ
  * `currencies::Vector{String}` : ["all"]または特定のセットに設定できます。たとえば、["LTC", "XTZ"]

# 例

```julia-repl
julia> show_all_accounts(user_data, ["LTC", "XTZ"])
2×7 DataFrame
 Row │ currency  balance  profile_id                         trading_enabled  id                                 hold  ⋯
     │ String    Float64  String                             Bool             String                             Float ⋯
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ LTC           0.0  4617f329-2709-453b-b95d-d14727cb…             true  eed5095d-848e-490c-8738-2f2073e7…      0 ⋯
   2 │ XTZ           0.0  4617f329-2709-453b-b95d-d14727cb…             true  21f6c731-91f7-44bf-ad9e-97cc2dfb…      0
```
