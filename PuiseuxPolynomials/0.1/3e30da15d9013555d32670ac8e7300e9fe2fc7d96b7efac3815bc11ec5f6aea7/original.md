`@Monomial x,y`

is  equivalent to `(x,y)=Monomial(:x,:y)` excepted  it creates `x,y` in the global scope of the current module, since it uses `eval`.
