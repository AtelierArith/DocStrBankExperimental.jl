```
hotspotq(imagefile, xs, ys=(0,1); label="", hint="", explanation="",
    correct_answer=nothing)
```

Question type to check if user clicks in a specified region of an image.

  * `imgfile`: File of an image. The images will be encoded and embedded in the web page.
  * `xs`: iterable specifying `(xmin, xmax)` with `0 <= xmin <= xmax <= 1`
  * `ys`: iterable specifying `(ymin, ymax)`
  * `correct_answer`: A text snippet of JavaScript which can be specified to add more complicated logic to test if an answer is correct. It must use `x` and `y` for the coordinates of the click.

## Examples

```
using Plots
p1 = plot(x -> x^2, axis=nothing, legend=false)
p2 = plot(x -> x^3, axis=nothing, legend=false)
p3 = plot(x -> -x^2, axis=nothing, legend=false)
p4 = plot(x -> -x^3, axis=nothing, legend=false)
l = @layout [a b; c d]
p = plot(p1, p2, p3, p4, layout=l)
imgfile = tempname() * ".png"
savefig(p, imgfile)
hotspotq(imgfile, (0,1/2), (0, 1/2), label="What best matches the graph of ``f(x) = -x^4``?")
```

!!! note
    The display of the image is not adjusted by this question type and must be managed separately.

