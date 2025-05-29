```
busywait(seconds)
```

Base.sleep()とは異なり、指定された秒数の間スレッドを最大限に活用します。最小のbusywait時間は1ミリ秒または入力の`0.001`です。
