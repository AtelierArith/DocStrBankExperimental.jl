TheoryMaps are morphisms in a category of GATs. A TheoryMap X -> Y can be  thought of in many ways.

1. An "Every model of Y is also a model of X in some way"
2. Providing "X-shaped hooks" into Y.
3. X is a syntax for Y's semantics.

The main methods for an AbsTheoryMap to implement are: 

  * dom, codom,
  * typemap: A dictionary of Ident (of AlgTypeConstructor in domain) to          TypeInCtx (The TypeScope of the TypeInCtx must be structurally           identical to the localcontext of the type constructor           associated with the key).
  * termmap: A dictionary of Ident (of AlgTermConstructor in domain) to           TermInCtx. (The TypeScope of the TrmInCtx must be structurally           identical to the localcontext + args of the term constructor           associated with the key.)

The requirement that the values of `typemap` and `termmap` be structurally  identical to the contexts in the domain can eventually be relaxed (to allow  reordering, additional derived elements, dropping unused arguments), but for now  we require this for simplicity.
