`RS2q(z::Vector{Float64}, R::Number, S::Number)`

`RS2q` computes the feed quality of a distillation column using the McCabe-Thiele method given the compositions of the products and the feed, the reflux ratio at the bottom of the column and the reflux ratio at the top of the column.

If feed is a saturated liquid, feed quality q = 1, feed quality is reset to q = 1 - 1e-10.

`RS2q` is a main function of the `McCabeThiele` toolbox for Julia.

See also: `stages`, `refmin`, `qR2S`, `qS2R`.

# Examples

Compute the the feed quality given the composition of the distillate is 88 %, the composition of the feed is 46 %, the composition of the column's bottom product is 11 %, the reflux ratio at the top of the column is 2 and reflux ratio at the bottom of the column is 2.5:

```
x=[0.88;0.46;0.11];
R=2;
S=2.5;
q=RS2q(x,R,S)
```
