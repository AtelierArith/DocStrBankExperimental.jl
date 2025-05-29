```
add_controller!(canvas, controller, domain, [init_state];
                show_controls::Bool=false)
```

指定されたPDDL `domain`の`canvas`に`controller`を追加します。再起動機能を有効にするために初期状態`init_state`を指定できます。
