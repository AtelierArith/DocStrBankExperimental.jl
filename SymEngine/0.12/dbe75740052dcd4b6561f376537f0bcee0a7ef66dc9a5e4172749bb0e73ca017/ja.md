```
subs
```

シンボリック表現に値を代入します。

例

```
@vars x y
ex = x^2 + y^2
subs(ex, x, 1) # 1 + y^2
subs(ex, (x, 1)) # 1 + y^2
subs(ex, (x, 1), (y,x)) # 1 + x^2, 値は左から右に代入されます。
subs(ex, x=>1)  # subs(x, (x,1)) の代替
subs(ex, x=>1, y=>1) # 同様
```
