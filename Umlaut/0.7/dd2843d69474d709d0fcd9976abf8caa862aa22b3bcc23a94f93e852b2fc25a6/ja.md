```
mkcall(fn, args...; val=missing, kwargs=(;))
```

Call操作の便利なコンストラクタです。valが`UncalculatedValue`（デフォルト）であり、呼び出し値が（束縛された）変数や定数から計算できる場合、それらは計算されます。この動作を防ぐためには、valを中立的な値に設定してください。
