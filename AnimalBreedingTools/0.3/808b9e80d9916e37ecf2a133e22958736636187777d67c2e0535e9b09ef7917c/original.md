```
disp(x)
disp(x...)
disp(io::IO,x)
disp(io::IO,x...)
disp(m::Array; format)
disp(io::IO, m::Array; format)
```

Write an object `x` (or objects `x...`) to `io` (or `stdout` if `io` is not given). The output is the same as `println` and `Base.print_matrix`, but the element type will not be shown. If an array is given, you can specify the C-style format with `format`.

```juliadoctests
A = [1 2; 3 4]
b = [9,10]

disp(A)
disp(b)
disp(A,b)
```
