```
clean(content::String)
```

表示されたページで見えるHTMLの部分のみを返します。これは、読者が変更を見たときにページが変更されたと仮定しており、これは合理的な仮定のようです。ただし、この仮定は、要素がJavascriptを介して動的に更新される場合に違反される可能性があることに注意してください。
