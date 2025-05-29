```
get_todays_forecast(;regional::Bool=false, region::AbstractString="")
```

クエリが呼び出された日の48時間の予測と実際の炭素強度のデータフレームを返します。デフォルトでは国レベルのデータを返します。地域的な空間解像度のデータを返すには、`regional=true`を渡します。単一の地域のデータを取得するには、`region = <desired region>`を渡します。ここで、<desired region>は`AVAILABLE_REGIONS`に含まれている必要があります。
