```
filter_events(flight::Symbol, df_event::DataFrame;
              keyword::String = "",
              tt_lim::Tuple   = ())
```

フライト中のイベントのDataFrameをフィルタリングして、関連するイベントのみを含むようにします。

**引数:**

  * `flight`:   フライト名（例: `:Flt1001`）
  * `df_event`: フライト中のイベントのルックアップテーブル（DataFrame）

| **フィールド** | **型**    | **説明**               |
|:--------- |:-------- |:-------------------- |
| `flight`  | `Symbol` | フライト名（例: `:Flt1001`） |
| `tt`      | `Real`   | `event`の時間 [s]       |
| `event`   | `String` | イベントの説明              |

  * `keyword`:  （オプション）イベント内で検索するキーワード、大文字小文字を区別しない
  * `tt_lim`:   （オプション）長さ`2`の開始および終了時間制限（含む） [s]

**戻り値:**

  * `df_event`: フライト中のイベントのルックアップテーブル（DataFrame）、フィルタリング済み
