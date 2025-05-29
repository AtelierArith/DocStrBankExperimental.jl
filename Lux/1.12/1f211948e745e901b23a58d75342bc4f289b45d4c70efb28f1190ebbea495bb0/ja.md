```
set_dispatch_doctor_preferences!(mode::String)
set_dispatch_doctor_preferences!(; luxcore::String="disable", luxlib::String="disable")
```

`LuxCore` と `LuxLib` パッケージのディスパッチドクターの設定を行います。

`mode` は `"disable"`、`"warn"`、または `"error"` のいずれかです。異なるモードの詳細については、[DispatchDoctor.jl](https://astroautomata.com/DispatchDoctor.jl/dev/) のドキュメントを参照してください。

設定がすでに行われている場合は、何も行われません。そうでない場合は、設定が行われます。変更を有効にするには、Julia セッションを再起動する必要があります。
