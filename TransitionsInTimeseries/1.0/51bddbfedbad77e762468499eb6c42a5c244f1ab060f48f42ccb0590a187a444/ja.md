```
WindowViewer(x; width, stride)
```

与えられた時系列 `x` に対して、指定された `width` のウィンドウに基づいてビューを生成するイテレータを初期化します。ウィンドウビューは、指定された `stride` で増加します。これを `map` と直接使用することができ、例えば `map(std, WindowViewer(x, ...))` は `x` の `std` の移動ウィンドウ時系列を提供します。

指定されていない場合、キーワード `width, stride` はそれぞれ `default_window_width(x)` と `1` として取られます。
