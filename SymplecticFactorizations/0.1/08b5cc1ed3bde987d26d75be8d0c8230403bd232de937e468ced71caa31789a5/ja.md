```
issymplectic(form::Symplecticform, x::AbstractMatrix; atol=0.0, rtol=atol)
issymplectic(x::Symplectic; atol=0.0, rtol=atol)
```

入力行列がシンプレクティックかどうかを返します。キーワード引数 `atol` と `rtol` は、それぞれチェックの絶対および相対許容誤差を決定するために呼び出すことができます。
