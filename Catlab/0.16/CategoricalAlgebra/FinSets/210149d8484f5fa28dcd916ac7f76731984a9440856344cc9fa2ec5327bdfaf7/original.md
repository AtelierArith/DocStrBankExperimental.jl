Limit of finite sets viewed as a table.

Any limit of finite sets can be canonically viewed as a table ([`TabularSet`](@ref)) whose columns are the legs of the limit cone and whose rows correspond to elements of the limit object. To construct this table from an already computed limit, call `TabularLimit(::AbstractLimit; ...)`. The column names of the table are given by the optional argument `names`.

In this tabular form, applying the universal property of the limit is trivial since it is just tupling. Thus, this representation can be useful when the original limit algorithm does not support efficient application of the universal property. On the other hand, this representation has the disadvantage of generally making the element type of the limit set more complicated.
