```
radial_cut(r, Θ, h; narc::Int=197)
```

Renders a polygon representing a radial cut (like a radial stub with no metal). The polygon has to be subtracted from a ground plane.

The parameter `h` is made available in the method signature rather than `a` because the focus of the arc (top of polygon) can easily centered in a waveguide. If it is desirable to control `a` instead, use trig: `a/2 = h*tan(Θ/2)`.

Parameters as follows, where X marks the origin and (*nothing above the origin is part of the resulting polygon*):

```
                       Λ
                      /│\
                     / │ \
                    /  |  \
              .    /   │Θ/2\
             .    /    │----\
            /    /   h │     \
           /    /      │      \
          /    /       │       \
         r    /        │        \
        /    /         │         \
       /    /----------X----------\
      /    /{--------- a ---------}\
     .    /                         \
    .    /                           \
        /                             \
       /                               \
      /                                 \
      --┐                             ┌--
        └--┐                       ┌--┘
           └--┐                 ┌--┘
              └--┐           ┌--┘
                 └-----------┘
                 (circular arc)
```
