`qS2R(z::Vector{Float64}, q::Number, S::Number)`

`qS2R` computes the reflux ratio at the top of a distillation column using the McCabe-Thiele method given the compositions of the products and the feed, the feed quality and the reflux ratio at the bottom of the column.

If feed is a saturated liquid, feed quality q = 1, feed quality is reset to q = 1 - 1e-10.

`qS2R` is a main function of the `McCabeThiele` toolbox for Julia.

See also: `stages`, `refmin`, `qR2S`, `RS2q`.

# Examples

Compute the reflux ratio at the top of the column given the composition of the distillate is 88 %, the composition of the feed is 46 %, the composition of the column's bottom product is 11 %, the feed is saturated liquid and the reflux ratio at the bottom of the column is 2.5:

```
x=[0.88;0.46;0.11];
q=1;
S=2.5;
R=qS2R(x,q,S)
```
