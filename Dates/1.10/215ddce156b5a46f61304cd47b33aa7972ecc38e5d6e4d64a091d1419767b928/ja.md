```
`Time`を調整APIを通じて作成します。出発点は提供された`h, mi, s, ms, us`引数から構築され、`f::Function`が`true`を返すまで調整されます。調整のステップサイズは`step`キーワードを通じて手動で提供できます。`limit`は、`f::Function`が満たされない場合にエラーをスローする前に調整APIが追求する最大反復回数の制限を提供します。デフォルトのステップは、与えられた引数に対してより高い精度を許可するように調整されることに注意してください。すなわち、時間、分、秒の引数が提供される場合、デフォルトのステップは`Second(1)`ではなく`Millisecond(1)`になります。

# 例

```

jldoctest julia> Time(t -> minute(t) == 30, 20) 20:30:00

julia> Time(t -> minute(t) == 0, 20) 20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5) ERROR: ArgumentError: 調整制限に達しました: 5回の反復 Stacktrace: [...] ```
