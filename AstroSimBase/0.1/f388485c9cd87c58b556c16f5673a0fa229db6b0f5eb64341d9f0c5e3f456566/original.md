function randin(T, a, b) function randin(a, b)

Generate uniform random number in `[a,b]`. It avoids error from `rand(a:b)` where `a` and `b` are `Unitful.Quantity`
