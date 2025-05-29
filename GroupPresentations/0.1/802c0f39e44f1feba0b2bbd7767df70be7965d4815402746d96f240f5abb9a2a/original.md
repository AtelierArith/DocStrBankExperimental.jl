`tracing(P::Presentation,stop=false)`

a  sequence of  Tietze transformations  applied to  a presentation `P₁` and ending  up with a presentation `P₂`, defines an isomorphism `φ` between the groups defined by `P₁` and `P₂`, respectively. To know `φ` (resp. `φ⁻¹`) we need  to  know  `φ(old  generators)`  or  `φ⁻¹(new generators)`. The Tietze transformations  functions  can  trace  these  images.  This is not done by default  since the involved words may grow to tremendous length; it will be done  on request  by calling  `tracing(P)`. A  call `tracing(P,false)` will stop tracing.

`tracing` initializes three fields of `P`:

`P.oldGenerators`:  is  initialized  to  a  copy of `P.generators`.

`P.imagesOldGens`:  is the list `φ(old generators)`  as Tietze words in the new generators. Its `i`-th entry is initialized to the Tietze word |[i]|.

`P.preImagesNewGens`: The list `φ⁻¹(new generators)` as Tietze words in the old generators. Its `i`-th entry is initialized by the Tietze word |[i]|.

The  existence of  these fields  will cause  the Tietze  transformations to update the lists `imagesOldGens` and `preImagesNewGens`.

There are a few restrictions concerning the tracing of generator images:

The  functions `AddGenerator`, `AddRelator`, and `RemoveRelator` may change the  isomorphism type  of the  presentation. Therefore,  if any  of them is called, it will call `tracing(P,false)`.

You  can reinitialize  tracing at  any later  state by  calling `tracing()` again: if the above fields do already exist when `tracing` is being called, they will be initialized again.
