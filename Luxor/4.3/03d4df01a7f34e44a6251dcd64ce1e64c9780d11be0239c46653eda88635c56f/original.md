```
circlering(o_center, o_radius, count=3)
```

Find `count` circles that fit inside an imaginary circle centered at o_center with radius and are tangent to it.

Returns:

  * an array of center/radius tuples defining each of the circles
  * a single center/radius tuple defining the circle that fits inside the calculated circles

```julia
cs, ic = circlering(Point(0, 0), 200, 3)

(Tuple
    [(Point(-53.59246086870698, 92.82486512724742), 92.815078262586),
     (Point(-53.59246086870705, -92.82486512724739), 92.815078262586),
     (Point(107.184921737414, -2.6252734264516723e-14), 92.815078262586)
   ],
    (Point(0.0, 0.0), 14.369843474828002))

@draw begin
    cs, ic = circlering(Point(0, 0), 200, 3)
    map(c -> circle(first(c), last(c), :fill), cs)
    circle(first(ic), last(ic), :fill)
end
```
