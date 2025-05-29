### CarouselArray{T}

  * dims::Vector{T}

A `CarouselArray` is an Array that can be indexed infinitely to one side or another. The indexes will roll over into the other end of the `Vector` stored within "dims".

##### example

```
mycarousel = CarouselArray([5, 10, 15, 20])

mycarousel[1]
5
mycarousel[0]
20
mycarousel[-1]
15
mycarousel[4]
20
mycarousel[5]
5
```

---

##### field info

  * **dims** - The inner `Vector` of a `CarouselArray`.

---

##### constructors

  * CarouselArray{T}()
  * CarouselArray{T}(x::AbstractVector)
  * CarouselArray(x::AbstractVector)
