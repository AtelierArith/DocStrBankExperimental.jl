```
WebPage(url::AbstractString; selector::Function=clean) <: Page
```

`url`でスキャンされるWebPage。`selector`は、ページの特定の領域のみを変更のためにスキャンするために使用できる関数です。デフォルトでは、`body`のみが考慮されます。ページ全体を取得するには、`selector=identity`を渡してください。
