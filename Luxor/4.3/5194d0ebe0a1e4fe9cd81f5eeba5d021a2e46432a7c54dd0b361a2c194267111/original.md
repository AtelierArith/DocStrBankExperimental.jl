```
textcurvecentered(the_text, the_angle, the_radius, center::Point;
      clockwise = true,
      letter_spacing = 0,
      baselineshift = 0
```

This version of the `textcurve()` function is designed for shorter text strings that need positioning around a circle. (A cheesy effect much beloved of hipster brands and retronauts.)

`letter_spacing` adjusts the tracking/space between chars, tighter is (-), looser is (+)). `baselineshift` moves the text up or down away from the baseline.

`textcurvecentred` (UK spelling) is a synonym.
