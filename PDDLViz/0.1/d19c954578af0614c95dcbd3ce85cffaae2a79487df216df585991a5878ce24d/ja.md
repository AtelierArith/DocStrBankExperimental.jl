```
KeyboardController(options...)
KeyboardController(
    key1 => act1, key2 => act2, ...,
    extra_key1, extra_key2, ...;
    exclusive=true, callback=nothing
)
```

キーボード入力をPDDLアクションにマッピングするコントローラーです。アクションを記録するには、`callback`を[`ControlRecorder`](@ref)に設定します。

# オプション

  * `keymap`: キーボードキーをPDDLアクションにマッピングする辞書。
  * `extrakeys`: 残りの利用可能なアクションにマッピングされたキー（デフォルト：数字キー）。
  * `extraprocess`: 残りのアクションをフィルタリング/処理する関数 `(state, acts) -> acts`。
  * `restart_key`: 初期状態が指定されている場合の再起動ボタン。
  * `exclusive`: 他のキーが押されていない場合にのみアクションが実行されるかどうか。
  * `callback`: アクション後のコールバック `f(canvas, domain, state, act, next_state)`。
  * `obsfunc`
