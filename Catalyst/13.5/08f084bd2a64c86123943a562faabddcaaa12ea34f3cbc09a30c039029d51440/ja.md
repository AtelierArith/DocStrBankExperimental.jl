```
conservationlaws(rs::ReactionSystem)
```

与えられた `ReactionSystem` の保存則行列を返します。システム内にまだ保存されていない場合は計算し、保存します。また、エイリアスを返します。

注意:

  * 初めて呼び出されたときに計算され、`rn` にキャッシュされます。以降の呼び出しは高速であるべきです。
