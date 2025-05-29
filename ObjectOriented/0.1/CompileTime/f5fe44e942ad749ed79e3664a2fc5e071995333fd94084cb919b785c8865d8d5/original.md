define (abstract) properties such as getters and setters:

```
## Abstract
@oodef struct IXXX
    @property(field) do
        get
        set
    end
end

## Concrete
@oodef struct XXX1 <: IXXX
    @property(field) do
        get = self -> 1
        set = (self, value) -> ()
    end
end
```
