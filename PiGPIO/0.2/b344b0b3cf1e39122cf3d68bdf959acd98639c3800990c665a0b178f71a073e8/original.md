```
get_mode(self::Pi, gpio)
```

Returns the GPIO mode for the pin `gpio` (integer between 0 and 53).

Returns a value as follows:

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
