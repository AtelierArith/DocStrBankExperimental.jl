```
add_event_handler!(fn, m, event)
```

指定されたモデルのためのイベントハンドラーを追加します。`event`はイベントに対応する`Symbol`でなければなりません。`fn`はそのイベントに対応する引数で呼び出せる関数でなければなりません。以下はイベント、引数、およびそれが発火するタイミングの表です。

|                    event | arguments |          when does it fire |
| ------------------------:| ---------:| --------------------------:|
|           `:model_built` |       `m` |            モデル`m`が構築された直後。 |
|  `:model_about_to_solve` |       `m` |             モデル`m`が解かれる直前。 |
|          `:model_solved` |       `m` |             モデル`m`が解かれた直後。 |
| `:window_about_to_solve` |  `(m, k)` |    モデル`m`のウィンドウ`k`が解かれる直前。 |
|         `:window_solved` |  `(m, k)` |    モデル`m`のウィンドウ`k`が解かれた直後。 |
|         `:window_failed` |  `(m, k)` | モデル`m`のウィンドウ`k`が解決に失敗した直後。 |

# 例

```julia
run_spineopt("sqlite:///path-to-input-db", "sqlite:///path-to-output-db") do m
    add_event_handler!(println, m, :model_built)  # モデルが構築された直後に出力する
end
```
