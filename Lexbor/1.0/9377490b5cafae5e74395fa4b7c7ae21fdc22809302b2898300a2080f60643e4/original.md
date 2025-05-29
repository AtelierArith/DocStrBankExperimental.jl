```
query(document | node, selector; first = false, root = false) -> Node[]
query(f, document | node, selector; first = false, root = false) -> nothing
```

Query the `document` or `node` for the given CSS `selector`. When `f` is provided then call `f` on each match that is found and return `nothing` from `query`. When no `f` is provided then just return a `Vector{Node}` containing all matches.

The `first::Bool` keyword controls whether to only match the first of a selector list. To quote the upstream documentation:

> Stop searching after the first match with any of the selectors in the list.
>
> By default, the callback will be triggered for each selector list. That is, if your node matches different selector lists, it will be returned multiple times in the callback.
>
> For example:
>
> ```plaintext
> HTML: <div id="ok"><span>test</span></div>
> Selectors: div, div[id="ok"], div:has(:not(a))
> ```
>
> The default behavior will cause three callbacks with the same node (div). Because it will be found by every selector in the list.
>
> This option allows you to end the element check after the first match on any of the selectors. That is, the callback will be called only once for example above. This way we get rid of duplicates in the search.


The `root::Bool` keyword controls whether to include the root node in the search. To quote the upstream documentation:

> Includes the passed (root) node in the search.
>
> By default, the root node does not participate in selector searches, only its children.
>
> This behavior is logical, if you have found a node and then you want to search for other nodes in it, you don't need to check it again.
>
> But there are cases when it is necessary for root node to participate in the search.  That's what this option is for.

