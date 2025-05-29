シンプルなアクティブパターンの実装です。`@active`の最初の引数に修飾子を指定することで、他のモジュールでの可視性をカスタマイズできます。

```julia
    @active F(x) begin
        if x > 0
            nothing
        else
            :ok
        end
    end

    @match -1 begin
        F(:ok) => false
        _ => true
    end # true

    @active public IsEven(x) begin
        x % 2 === 0
    end

    @match 4 begin
        IsEven() => :ok
        _ => :err
    end # :ok
```
