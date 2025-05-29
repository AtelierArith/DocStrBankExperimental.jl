```
sconnect(input::Function, sys::T; name)
sconnect(input::Num,      sys::T; name)
```

関数 `input(t)` を `sys.input` に接続します

# 例:

```julia
sconnect(sin, sys)   # 時間の関数であると仮定して関数を接続します
sconnect(sin(t), sys) # Num を接続します
```
