## One-argument form

```
@unroll expr
```

Unrolls the following constructs in expr :

```
for i in start:stop ... end
(expr for i in start:stop)
sum(expr for i=start:stop ... end)
```

provided integers `start` and `stop` are known at *parse* time. Unrolling applies recursively to sub-expressions contained in `expr`.

!!! example
    ```
    @unroll for i=4:6 ; foo(i); end
    @unroll (i*i for i=4:6)
    @unroll sum(i * i for i=4:6)
    ```

    expands to

    ```
    begin; foo(4); foo(5); foo(6) ; end
    (4*4, 5*5, 6*6)
    4*4 + 5*5 + 6*6
    ```


## Two-argument form

```
@unroll n in start:stop expr(n)
```

Expands to

```
if n==start ; @unroll expr(start) ; end
if n==start+1 ; @unroll expr(start+1) ; end
...
if n==stop ; @unroll expr(stop) ; end
```

provided integers `start` and `stop` are known at parse time. Unrolling applies recursively `expr` and its sub-expressions.

!!! warning
    Nested use of @unroll should never be necessary, is not supported and may not work as expected.

