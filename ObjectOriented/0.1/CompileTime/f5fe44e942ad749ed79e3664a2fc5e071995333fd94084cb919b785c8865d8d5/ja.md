```
## 抽象
@oodef struct IXXX
    @property(field) do
        get
        set
    end
end

## 具体
@oodef struct XXX1 <: IXXX
    @property(field) do
        get = self -> 1
        set = (self, value) -> ()
    end
end
```
