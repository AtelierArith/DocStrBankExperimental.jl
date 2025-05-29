Simple active pattern implementation. You can give a qualifier in the first argument of `@active` to customize its visibility in other modules.

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
