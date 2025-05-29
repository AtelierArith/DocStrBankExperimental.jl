```
apply(body::Function, patches) -> Any
```

`body`の実行中に1つ以上の`patches`を適用します。具体的には、`body`を実行中に遭遇したすべての[`@mock`](@ref)呼び出しサイトは、ディスパッチを行う際に提供された`patches`を含みます。

複数のパッチを利用する際には、どのメソッドを呼び出すかを決定するために多重ディスパッチが使用されます。ただし、パッチで定義されたメソッドは、元の関数メソッドよりも常に優先されます。

!!! note
    [`apply`](@ref)を呼び出す前に[`activate`](@ref)を呼び出していることを確認してください。そうしないと、提供されたパッチは無視されます。


関連情報: [`@mock`](@ref), [`@patch`](@ref).

## 例

パッチを適用すると、代替のパッチ関数が呼び出されます：

```jldoctest
julia> f() = "original";

julia> p = @patch f() = "patched";

julia> apply(p) do
            @mock f()
       end
"patched"
```

パッチは、元のメソッドがより特異的であっても、元の関数よりも優先されます：

```jldoctest
julia> f(::Int) = "original";

julia> p = @patch f(::Any) = "patched";

julia> apply(p) do
            @mock f(1)
       end
"patched"
```

ただし、パッチが呼び出すための有効なメソッドを提供しない場合は、元の関数がフォールバックとして使用されます：

```jldoctest
julia> f(::Int) = "original";

julia> p = @patch f(::Char) = "patched";

julia> apply(p) do
           @mock f(1)
       end
"original"
```

### ネスティング

複数の[`apply`](@ref)呼び出しをネストすることが許可されています。同じメソッドに対して複数のパッチが提供される場合、最も内側のパッチが優先されます：

```jldoctest
julia> f() = "original";

julia> p1 = @patch f() = "p1";

julia> p2 = @patch f() = "p2";

julia> apply(p1) do
           apply(p2) do
               @mock f()
           end
       end
"p2"
```

異なるメソッドに対して複数のパッチが提供される場合、最も特異的なパッチを選択するために多重ディスパッチが使用されます：

```jldoctest
julia> f(::Int) = "original";

julia> p1 = @patch f(::Integer) = "p1";

julia> p2 = @patch f(::Number) = "p2";

julia> apply(p1) do
           apply(p2) do
               @mock f(1)
           end
       end
"p1"
```
