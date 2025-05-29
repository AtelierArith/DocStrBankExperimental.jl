`AlgAccessor`

The arguments to a term constructor serve a dual function as both arguments and also methods to extract the value of those arguments.

I.e., declaring `Hom(dom::Ob, codom::Ob)::TYPE` implicitly overloads a previous declaration for `dom` and `codom`, or creates declarations if none previously exist.
