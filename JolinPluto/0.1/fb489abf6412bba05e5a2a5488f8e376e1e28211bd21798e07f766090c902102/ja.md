```
repeat_at(t -> (rand(), t), ceil(now(), Second(10)), init=:wait)

repeat_at(ceil(now(), Second(10)), init=:wait) do t
	# 繰り返し返されるコード
	rand(), t
end
```

Pluto内で実行すると、指定された次の時間に関数が再実行され、何度も繰り返されます。

## キーワード引数

  * `init`は、最初の実行または標準的な反応性によって引き起こされる再評価時に何をするかを指定します。任意の関数（例：`init=myinit_func`）または2つの特別な値のいずれかで指定できます：`:wait`または`:run`。`:wait`（デフォルト）は次の時間を待ってからコードを実行します。`:run`は待たずにコードを即座に実行します。
