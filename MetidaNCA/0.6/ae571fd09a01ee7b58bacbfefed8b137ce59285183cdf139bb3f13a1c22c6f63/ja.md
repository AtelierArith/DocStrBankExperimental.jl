```
pkimport(data, time, obs, sort;
    kelauto = true,
    elimrange = ElimRange(),
    dosetime = DoseTime(),
    limitrule::Union{Nothing, LimitRule} = nothing,
    warn = true,
    kwargs...)
```

テーブル `data` から PK データをインポートします。

  * `time` - 時間列;
  * `obs` - 濃度列;
  * `sort` - 被験者のソート列。

キーワード:

  * `kelauto` - `true` の場合は自動範囲設定、`false` の場合は `elimrange` から `kelstart`/`kelend` を使用;
  * `elimrange` - 排除範囲設定を設定;
  * `dosetime` - 投与量と投与時間を設定、デフォルトでは dosetime = 0、投与量は `NaN`;
  * `limitrule` - 被験者に limitrule を適用;
  * `warn` - 警告を抑制するには false;
  * checktime (true) - 時間値の一意性をチェック;
  * nutcfunk (last) - 同一時間の濃度値を選択するために使用される関数 (checktime == `true` の場合)。

!!! note
    時間列に非一意の値がある場合は、最後のペアの時間-濃度が使用されます。


関連情報: [`ElimRange`](@ref), [`DoseTime`](@ref), [`LimitRule`](@ref).
