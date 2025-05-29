```
@pyconvert(T, x, [onfail])
```

Pythonオブジェクト`x`を`T`に変換します。

失敗した場合、`onfail`に評価され、デフォルトでは`return pyconvert_unconverted()`になります（主に変換ルールを書くために便利です）。
