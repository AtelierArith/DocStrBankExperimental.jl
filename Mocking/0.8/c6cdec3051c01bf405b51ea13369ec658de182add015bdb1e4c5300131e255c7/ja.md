```
@mock expr
```

呼び出し元の関数を適用されたパッチを介して一時的にオーバーロードすることを可能にします。

`@mock` マクロは、`Mocking.activate` が呼び出されるまでノーオプとして機能します。Mocking がアクティブ化されると、[`@patch`](@ref) を介して定義された代替メソッドを [`apply`](@ref) と共に使用して、`apply` コンテキスト内からパッチされたメソッドを呼び出すことができます。

関連情報: [`@patch`](@ref), [`apply`](@ref).

## 例

```jldoctest; setup=:(using Dates: Dates)
julia> f() = @mock time();

julia> p = @patch time() = 0.0;  # UNIX エポック

julia> apply(p) do
           Dates.unix2datetime(f())
       end
1970-01-01T00:00:00
```
