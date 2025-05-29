```
polysuper(center::Point = Point(0, 0);
    n1 = 1,
    n2 = 1,
    n3 = 1,
    m = 2,
    a = 1,
    b = 1,
    radius = 100,
    action = :none,
    vertices = false,
    reversepath = false,
    stepby = π / 120)
```

Build a supershape, a generalization of the superellipse, and apply `action`.

Based upon equations by Johan Gielis.

See also: `squircle()`...

## Example

```julia
polysuper(m=4,
    n1=13, n2=11, n3=3,
    a=3, b=4,
    action=:fill,
    radius=200)
```

produces a weird eye/lemon shape, a bit like this:

```plain
                        @@@@@@S
                  @@@@@@@@@@@@@@@@@@
               @@@@@@@@@@@@@@@@@@@@@@@@
            R@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
          @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
      @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
   @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
     @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
         @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
            @@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
              E@@@@@@@@@@@@@@@@@@@@@@@@@
                  @@@@@@@@@@@@@@@@@@o
                      @@@@@@@@@@
```
