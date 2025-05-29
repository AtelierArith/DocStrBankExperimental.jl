```
get_mode(self::Pi, gpio)
```

GPIOピン`gpio`のモードを返します（0から53の間の整数）。

次のような値を返します：

```
0 = INPUT
1 = OUTPUT
2 = ALT5
3 = ALT4
4 = ALT0
5 = ALT1
6 = ALT2
7 = ALT3
```

```julia
print(get_mode(pi, 0))
# output 4
```
