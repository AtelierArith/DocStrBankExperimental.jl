```
show_next_transition(io::IO=stdout, zdt::ZonedDateTime)
show_next_transition(io::IO=stdout, tz::TimeZone=localzone())
```

次のタイムゾーンの遷移に関する有用な情報を表示します（通常は夏時間によるものです）。表示される情報には以下が含まれます：

  * 遷移日：遷移が発生するローカルの日付（2018-10-28）
  * ローカル時間の変更：ローカル時計がどのように変更されるか（02:00が01:00に戻る）および変更の方向（「前進」または「後退」）
  * オフセットの変更：遷移の前後で発生する標準オフセットとDSTオフセット
  * 遷移前：遷移が発生する直前の瞬間
  * 遷移後：遷移が発生した直後の瞬間

```julia
julia> show_next_transition(ZonedDateTime(2018, 8, 1, tz"Europe/London"))
Transition Date:   2018-10-28
Local Time Change: 02:00 → 01:00 (Backward)
Offset Change:     UTC+0/+1 → UTC+0/+0
Transition From:   2018-10-28T01:59:59.999+01:00 (BST)
Transition To:     2018-10-28T01:00:00.000+00:00 (GMT)

julia> show_next_transition(ZonedDateTime(2011, 12, 1, tz"Pacific/Apia"))
Transition Date:   2011-12-30
Local Time Change: 00:00 → 00:00 (Forward)
Offset Change:     UTC-11/+1 → UTC+13/+1
Transition From:   2011-12-29T23:59:59.999-10:00
Transition To:     2011-12-31T00:00:00.000+14:00
```
