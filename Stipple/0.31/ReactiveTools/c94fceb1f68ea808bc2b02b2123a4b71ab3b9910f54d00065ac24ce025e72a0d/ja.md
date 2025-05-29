```
@handler App expr
```

ReactiveModel App内から呼び出すことができるハンドラ関数を定義します。存在しない場合、マクロは変数`__model__`を最初の引数として追加します。

パラメータ:

  * `App`: 次のいずれか

      * ReactiveModel（例: `MyApp`）
      * リアクティブ変数のリスト（例: `(:r1, :r2)`）
      * リアクティブ変数のリストと非リアクティブ変数のリストのタプルまたはベクター（例: `((:r,), (:nr,))`）
  * `expr`: 関数定義、例: `function my_handler() println("n: $n") end`

### 例 1

```julia
@app MyApp begin
  @in i = 0
  @onchange i on_i()
    println("Hello World")
  end
end

@handler MyApp function on_i()
  println("i: $i")
end
```

### 例 2

```julia-repl
julia> @macroexpand @handler (:a,) function f() a end
quote
    function f(__model__)
        model.a[]
    end
end

julia> @macroexpand @handler ((:a,), (:b,)) function f(x, __model__) a, b end
quote
    function f(x, __model__)
        (__model__.a[], __model__.b)
    end
end
```
