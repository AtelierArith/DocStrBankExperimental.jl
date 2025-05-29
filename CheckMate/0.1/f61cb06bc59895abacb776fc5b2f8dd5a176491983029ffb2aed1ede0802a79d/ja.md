```
@checkset(name::String, block::Expr)::CheckSet
```

データ検証チェックの名前付きセットを作成します。

# 引数

  * `name`: チェックのセットの説明的な名前
  * `block`: @check 構文を使用したチェック定義のブロック

# 例

```julia
# チェック関数を定義します
function check_amount_positive(amount)
    amount > 0
end

function check_valid_currency(currency)
    currency in ("USD", "EUR", "GBP")
end

# チェックセットを作成します
checks = @checkset "Payment Validation" begin
    @check "Amount is positive" check_amount_positive(:amount)
    @check "Valid currency" check_valid_currency(:currency)
end
```

注意: チェック条件は名前付き関数として定義する必要があります。ラムダ式（例: `x -> x > 0`）はサポートされていません。
