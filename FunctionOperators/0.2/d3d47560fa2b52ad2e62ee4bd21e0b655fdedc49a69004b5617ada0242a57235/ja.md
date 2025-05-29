反復実行されるコードフラグメントを、途中結果のために割り当てられた配列を保持し、それを次の反復で再利用するようにコードを変換することで、行列操作が多い場合に速度を向上させます。

**最初のバリアント**:

```julia
@recycle <最適化されるコード>
```

**2番目のバリアント**:

```julia
@recycle(arrays = [<配列変数のリスト>], funops = [<FunOp変数のリスト>], numbers = [<数値変数のリスト>], <最適化されるコード>)
```

**最初のバリアント**は、変数の型を推測しようとするため、より便利です（他のバリアントは、ユーザーが明示的にArray、FunOp、およびNumberの型の変数のリストを宣言する必要があります）。その代償として、このバリアントは、最適化されたコードにクロージャまたは非定数のグローバル変数が含まれている場合に失敗します。

**2番目のバリアント**は、より柔軟（かつ冗長）で、ユーザーが明示的にArray、FunOp、およびNumberの型の変数のリストを宣言する必要があります。他のバリアントは変数の型を推測しようとするため、より便利ですが、その代償として、最適化されたコードにクロージャまたは非定数のグローバル変数が含まれている場合に失敗します。一方で、この（より冗長な）バリアントはこれらの制限から自由です。*注：すべての「キーワード引数」はオプションであり、その順序も任意です。*

最初のバリアントの例：この関数

```julia
function foo()
    A = rand(100,100)
    B = rand(100,100)
    @recycle for i = 1:5
        A += A / 2 + B
        C = A * B + 5
    end
end
```

は次のように変換されます：

```julia
function foo()
    A = rand(100,100)
    B = rand(100,100)
    (C, 🔃₂) = fill(nothing, 2)
    (is_first_run₁,) = fill(true, 1)
    for i = 1:5
        A .+= A ./ 2 .+ B
        if is_first_run₁
            is_first_run₁ = false
            🔃₂ = A * B
            C = 🔃₂ .+ 5
        else
            mul!(🔃₂, A, B)
            C .= 🔃₂ .+ 5
        end
    end
end
```

2番目のバリアントができることを示す別の例（最初のバリアントではできない）：

```julia
bar = @recycle(arrays=[A,B], (A, B) -> begin
    A += A / 2 + B
    B = A * B .+ 5
end)
function baz()
    A = rand(100,100)
    B = rand(100,100)
    for i = 1:5
        bar(A,B)
    end
end
```

は次のように変換されます：

```julia
bar = begin
    (🔃₁,) = fill(nothing, 1)
    (is_first_run₁,) = fill(true, 1)
    (A, B)->begin
            A .+= A ./ 2 .+ B
            begin
                if is_first_run₁
                    is_first_run₁ = false
                    🔃₁ = A * B
                else
                    mul!(🔃₁, A, B)
                end
                B .= 🔃₁ .+ 5
            end
        end
end
function baz()
    A = rand(100,100)
    B = rand(100,100)
    for i = 1:5
        bar(A,B)
    end
end
```
