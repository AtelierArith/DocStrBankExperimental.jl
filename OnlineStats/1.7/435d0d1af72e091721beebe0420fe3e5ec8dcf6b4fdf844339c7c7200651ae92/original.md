```
CallFun(o::OnlineStat, f::Function)
```

Call `f(o)` every time the OnlineStat `o` gets updated.

# Example

```
o = CallFun(Mean(), println)
fit!(o, [0,0,1,1])
```
