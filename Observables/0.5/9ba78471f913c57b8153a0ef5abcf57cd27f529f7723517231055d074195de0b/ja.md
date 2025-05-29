```
mutable struct ObserverFunction <: Function
```

フィールド:

```
f::Function
observable::AbstractObservable
weak::Bool
```

`ObserverFunction` は `on` の戻り値として意図されており、`weak` フラグが設定されている限り、ObserverFunction がスコープを外れるときに作成されたクロージャを `obsfunc.observable` のリスナーベクターから削除できます。`weak` フラグが設定されていない場合、ObserverFunction がスコープを外れても何も起こらず、安全に無視できます。それでも、後で接続を解除するために `off(observable, f)` の代わりに `off(obsfunc)` を呼び出す方が簡単なので、便利です。
