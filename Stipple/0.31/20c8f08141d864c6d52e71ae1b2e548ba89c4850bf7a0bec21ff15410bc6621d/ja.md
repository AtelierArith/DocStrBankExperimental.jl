```
onbutton(f::Function, button::R{Bool}; async = false, weak = false)
```

関数を反応的なブールパラメータにリンクします。通常、アプリのボタンを表します。関数が呼び出された後、パラメータは再びfalseに設定されます。`async`キーワードは、呼び出しを非同期に行うべきかどうかを指定します。

### 例

```julia
onbutton(model.save_button) do
  # 保存する必要があるものを保存
end
```
