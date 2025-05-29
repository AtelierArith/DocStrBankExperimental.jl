```
textcurve(the_text, start_angle, start_radius, pos;
      # optional keyword arguments:
      spiral_ring_step = 0,    # step out or in by this amount
      letter_spacing = 0,      # tracking/space between chars, tighter is (-), looser is (+)
      spiral_in_out_shift = 0, # + values go outwards, - values spiral inwards
      clockwise = true
      )
```

Place a string of text on a curve. It can spiral in or out.

`start_angle` is relative to +ve x-axis, arc/circle is centered on `pos` with radius `start_radius`.
