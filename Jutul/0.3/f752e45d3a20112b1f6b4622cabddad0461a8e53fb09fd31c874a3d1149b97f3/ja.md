関数を二次変数を更新するものとして指定します。

次に、一般的な評価者が定義され、その関数が状態に依存するものを取得するための関数が定義されます。これは例を用いて最も簡単に文書化できます。以下の関数を、あるモデルに対して実現された `MyVarType` の値を含む配列を更新する際にマクロで注釈を付けて定義するとします。

```julia
@jutul_secondary function some_fn!(target, var::MyVarType, model, a, b, c, ix)
    for i in ix
        target[i] = a[i] + b[i] / c[i]
    end
end
```

このマクロの目的は、これを2つの関数に変換することです。最初の関数は、状態のフィールド（主変数、副変数、およびパラメータ）に関する関数の依存関係を定義します。

```julia
function get_dependencies(var::MyVarType, model)
   return (:a, :b, :c)
end
```

2番目の関数は、状態を受け取り、依存関係のセットを `getfield` 呼び出しに自動的に展開する一般的なバージョンを定義します。

```julia
function update_secondary_variable!(array_target, var::MyVarType, model, state, ix)
    some_fn!(array_target, var, model, state.a, state.b, state.c, ix)
end
```

引数4からend-1までの入力名は重要であり、これらは状態から取得されるため、正確に書かれた通りになります。
