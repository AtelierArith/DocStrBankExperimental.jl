```
plot_events!(p1::Plot, flight::Symbol,  df_event::DataFrame;
             keyword::String = "",
             show_lab::Bool  = true,
             t0::Real        = 0,
             t_units::Symbol = :sec,
             legend::Symbol  = :outertopright)
```

既存のプロットにフライト中のイベントをプロットします。

**引数:**

  * `p1`:       プロット（すなわち、データの時系列）
  * `flight`:   フライト名（例: `:Flt1001`）
  * `df_event`: フライト中のイベントのルックアップテーブル（DataFrame）

| **フィールド** | **型**    | **説明**               |
|:--------- |:-------- |:-------------------- |
| `flight`  | `Symbol` | フライト名（例: `:Flt1001`） |
| `tt`      | `Real`   | `event` の時間 [s]      |
| `event`   | `String` | イベントの説明              |

  * `keyword`:  （オプション）イベント内で検索するキーワード、大文字小文字を区別しない
  * `show_lab`: （オプション）trueの場合、フライト中のイベント（凡例）ラベルを表示
  * `t0`:       （オプション）時間オフセット [`t_units`]
  * `t_units`:  （オプション）時間単位 {`:sec`,`:min`}
  * `legend`:   （オプション）凡例の位置（例: `:topleft`,`:outertopright`）

**戻り値:**

  * `nothing`: フライト中のイベントが `p1` にプロットされます
