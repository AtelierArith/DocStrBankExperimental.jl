```
BridgeElement(elementStart::Element, posStart::Float64, elementEnd::Element, posEnd::Float64, section::Section, id = :element; release = :fixedfixed)
```

Create a bridge element between two frame elements. Connects from `elementStart` at a position `elementStart.length * posStart` away from `elementStart.nodeStart.position` to `elementEnd` at `elementEnd.length * posEnd` away from `elementEnd.nodeStart.position`. IE `posStart, posEnd ∈ ]0, 1[`
