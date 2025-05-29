```
tight_bbox(gl::GridLayout)
```

現在の `GridLayout` の内容に対して適切な `suggestedbbox` となるバウンディングボックスを計算します。例えば、`GridLayout` に固定サイズのコンテンツやアスペクト制約のある列が含まれている場合、`GridLayout` の解決されたサイズはその `suggestedbbox` と異なる可能性があります。`tight_bbox` の結果を使用して、すべてのコンテンツが利用可能なスペースに収まるように `suggestedbbox` を調整できます（例えば、図をリサイズすることによって）。サイズには、`GridLayout` の `Outside` アラインモードからのパディングなど、可能なパディングが含まれます。
