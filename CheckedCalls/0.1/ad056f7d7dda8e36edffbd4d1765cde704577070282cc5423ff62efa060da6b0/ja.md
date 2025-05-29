```
checkedcall(f, args...)
checkedcall(f)
```

`f(args...)`を呼び出し、結果に異常がないかをチェックし、結果を返すか例外をスローします。

`checkedcall(f)(args...)`は`checkedcall(f, args...)`と同等です。

デフォルトでは、`containsnan`を使用して戻り値をチェックします。

異常の根本的な原因が不必要な計算オーバーヘッドなしにより正確に特定できる場合、`checkedcall`は特化すべきです。例えば、

```julia
chained(f, g, x) = f(g(x))
```

次のように特化したい場合があります。

```julia
function checkedcall(::typeof(chained), f, g, x)
    checkedcall(f, checkedcall(g, x))
end
```

`checkedcall`は、特定の関数に対して追加の出力（および入力）値チェックを実行するように特化することもでき、チェックは`NaN`値に限定する必要はありません。
