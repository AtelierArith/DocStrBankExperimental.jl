```
Node(instanceof, children...; props...)
Node(instanceof, children, props)
```

The building block of WebIO. A `Node` is simply a wrapper around an *instance* (some Julia object) together with some child nodes and additional properties.

The most common type of `Node` is a DOM node. These can be constructed just by specifying a symbol as the `instanceof` (they are promoted to an instance of `WebIO.DOM` under the hood).

```jldoctest
julia> Node(:div, Node(:p, "I am a paragraph!", class="important"))
(div
  (p { class="important" }
    "I am a paragraph!"))
```

Nodes with custom (non-`DOM`) instances should have a corresponding `WebIO.render` method defined.
