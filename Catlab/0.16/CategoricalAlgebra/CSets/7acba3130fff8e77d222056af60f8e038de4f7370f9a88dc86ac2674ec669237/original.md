A limit of a diagram of ACSets with LooseACSetTransformations.

For general diagram shapes, the apex of the categorical limit will not have clean Julia types for its attributes, i.e. predicates will be needed to further  constrain them. `product_attrs` must be turned on in order to avoid an error in  cases where predicates would be needed. 

`product_attrs=true` will take a limit of the purely combinatorial data, and  the attribute data of the apex is dictated purely by the ACSets that are have  explicit cone legs: the value of an attribute (e.g. `f`) for the i'th part in   the apex is the product `(f(π₁(i)), ..., f(πₙ(i)))` where π maps come from  the combinatorial part of the limit legs. The type components of the j'th leg of  the limit is just the j'th cartesian projection.
