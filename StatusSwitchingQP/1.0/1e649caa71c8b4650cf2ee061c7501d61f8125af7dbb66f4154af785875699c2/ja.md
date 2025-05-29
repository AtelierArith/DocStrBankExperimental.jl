```
    struct Event{T<:AbstractFloat}
```

資産が出入りするイベント（DNまたはUP）、または不等式が結びつく（EO、等式として）かどうか（OE、元の不等式）を示すフィールド：

```
        From::Status
        To::Status
        id::Int     #資産ID
        L::T        #L
```
