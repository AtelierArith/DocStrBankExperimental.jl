Every cell is a node in the reactive graph. The nodes/point/vertices are the *cells*, and the edges/lines/arrows are the *dependencies between cells*. In a reactive notebook, these dependencies are the **global variable references and definitions**. (For the mathies: a reactive notebook is represented by a *directed multigraph*. A notebook without reactivity errors is an *acyclic directed multigraph*.) This struct contains the back edges (`references`) and forward edges (`definitions`, `soft_definitions`, `funcdefs_with_signatures`, `funcdefs_without_signatures`) of a single node.

Before 0.12.0, we could have written this struct with just two fields: `references` and `definitions` (both of type `Set{Symbol}`) because we used variable names to form the reactive links. However, to support defining *multiple methods of the same function in different cells* (https://github.com/fonsp/Pluto.jl/issues/177), we needed to change this. You might want to think about this old behavior first (try it on paper) before reading on.

The essential idea is that edges are still formed by variable names. Simple global variables (`x = 1`) are registered by their name as `Symbol`, but *function definitions* `f(x::Int) = 5` are sometimes stored in two ways:

  * by their name (`f`) as `Symbol`, in `funcdefs_without_signatures`, and
  * by their name with its method signature as `FunctionNameSignaturePair`, in `funcdefs_with_signatures`.

The name *without* signature is most important: it is used to find the reactive dependencies between cells. The name *with* signature is needed to detect multiple cells that define methods with the *same* signature (`f(x) = 1` and `f(x) = 2`) - this is illegal. This is why we do not collect `definitions`, `funcdefs_with_signatures` and `funcdefs_without_signatures` onto a single pile: we need them separately for different searches.
