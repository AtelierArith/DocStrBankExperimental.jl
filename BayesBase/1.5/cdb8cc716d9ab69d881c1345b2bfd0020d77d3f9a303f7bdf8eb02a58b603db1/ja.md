```
clamplog(x)
```

`log`と同様ですが、入力引数`x`を`tiny <= x <= typemax(x)`の範囲に制限し、`log(0)`が爆発しないようにします。
