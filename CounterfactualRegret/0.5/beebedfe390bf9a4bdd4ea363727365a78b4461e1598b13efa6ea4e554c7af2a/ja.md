関数をラップし、`n` CFR イテレーションごとにトリガーされるようにします

```
test_cb = Throttle(() -> println("test"), 100)
```

上記の例では、`"test"` が 100 CFR イテレーションごとに印刷されます
