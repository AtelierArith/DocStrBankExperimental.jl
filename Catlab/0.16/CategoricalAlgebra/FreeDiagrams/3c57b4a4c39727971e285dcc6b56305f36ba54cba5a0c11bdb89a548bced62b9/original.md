Bundle together legs of a multi(co)span.

For example, calling `bundle_legs(span, SVector((1,2),(3,4)))` on a multispan with four legs gives a span whose left leg bundles legs 1 and 2 and whose right leg bundles legs 3 and 4. Note that in addition to bundling, this function can also permute legs and discard them.

The bundling is performed using the universal property of (co)products, which assumes that these (co)limits exist.
