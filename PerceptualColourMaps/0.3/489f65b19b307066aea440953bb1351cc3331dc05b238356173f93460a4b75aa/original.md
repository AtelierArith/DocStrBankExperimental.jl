sineramp  - Generates sine on a ramp colour map test image

The test image consists of a sine wave superimposed on a ramp function The amplitude of the sine wave is modulated from its full value at the top of the image to 0 at the bottom.

The image is useful for evaluating the effectiveness of different colour maps. Ideally the sine wave pattern should be equally discernible over the full range of the colour map.  In addition, across the bottom of the image, one should not see any identifiable features as the underlying signal is a smooth ramp.  In practice many colour maps have uneven perceptual contrast over their range and often include 'flat spots' of no perceptual contrast that can hide significant features.

```
Usage: img = sineramp(sze, amp, wavelen, p)
       img = sineramp()

Arguments:     sze - (rows, cols) specifying size of test image.
                     Defaults to (256 512)  Note the number of columns is
                     nominal and will be ajusted so that there are an
                     integer number of sine wave cycles across the image.
               amp - Amplitude of sine wave. Defaults to 12.5
           wavelen - Wavelength of sine wave in pixels. Defaults to 8.
                 p - Power to which the linear attenuation of amplitude,
                     from top to bottom, is raised.  For no attenuation use
                     p = 0.  For linear attenuation use a value of 1.  For
                     contrast sensitivity experiments use larger values of
                     p.  The default value is 2.
```

The ramp function that the sine wave is superimposed on is adjusted slightly for each row so that each row of the image spans the full data range of 0 to

255. Thus using a large sine wave amplitude will result in the ramp at the

top of the test image being reduced relative to the slope of the ramp at the bottom of the image.

To start with try

```
  > img = sineramp()
```

This is equivalent to

```
  > img = sineramp((256 512), 12.5, 8, 2)
```

View it under 'gray' then try the 'jet', 'hsv', 'hot' etc colour maps.  The results may cause you some concern!

If you are wishing to evaluate a cyclic colour map, say hsv, it is suggested that you use the test image generated by circlesineramp().

See source code comments for more details on the default wavelength and amplitude.

See also: circlesineramp, chirplin, chirpexp, equalisecolourmap, cmap
