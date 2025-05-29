cmap:  Library of perceptually uniform colour maps

Most of these colour maps have been designed to have constant a magnitude of lightness gradient.  At fine spatial frequencies perceptual contrast is dominated by *lightness* difference, chroma and hue are relatively unimportant.

```
Usage:  1:  map = cmap(I, keyword_params ...)
        2:  (map, name, desc) = cmap(I, keyword_params ..., returnname=true)
        3:  cmap(searchStr)
        4:  cmap()

Arguments for Usage 1 and 2:

            I - A string label indicating the colour map to be generated or a
                string specifying a colour map name or attribute to search
                for.  Type 'cmap()' with no arguments to get a full list of
                possible colour maps and their corresponding labels.

  labels:  "L1" - "L20"  for linear maps
           "D1" - "D13"  for diverging maps
           "C1" - "C11"  for cyclic maps
           "R1" - "R4"   for rainbow maps
           "I1" - "I3"   for isoluminant maps

  labels for generating maps for the colour blind:
           "CBL1"  - "CBL4" Linear maps for protanopic and deuteranopic viewers.
           "CBD1"  - "CBD2" Diverging maps for protanopic and deuteranopic viewers.
           "CBC1"  - "CBC2" Cyclic maps for protanopic and deuteranopic viewers.
           "CBTL1" - "CBTL4" Linear maps for tritanopic viewers.
           "CBTD1" - Diverging map for tritanopic viewers.
           "CBTC1" - "CBTC2" Cyclic maps for tritanopic viewers.


 Some colour maps have alternate labels for convenience and readability.

   map = cmap("L1")  or map = cmap("grey")  will produce a linear grey map.
   cmap()  lists all colour maps and labels.

 Possible keyword parameter options:

    chromaK::Real - The scaling to apply to the chroma values of the colour map,
                    0 - 1.  The default is 1 giving a fully saturated colour map
                    as designed. However, depending on your application you may
                    want a colour map with reduced chroma/saturation values.
                    You can use values greater than 1 however gamut clipping is
                    likely to occur giving rise to artifacts in the colour map.
           N::Int - Number of values in the colour map. Defaults to 256.
      shift::Real - Fraction of the colour map length N that the colour map is
                    to be cyclically rotated, may be negative.  (Should only be
                    applied to cyclic colour maps!). Defaults to 0.
    reverse::Bool - If true reverses the colour map. Defaults to false.
diagnostics::Bool - If true displays various diagnostic plots. Note the
                    diagnostic plots will be for the map _before_ any cyclic
                    shifting or reversing is applied. Defaults to false.
 returnname::Bool - If true the function returns a tuple of the colourmap, its
                    name and its description  (colourmap, name, description)
                    The default value is false, just the colourmap is returned.

Returns:
          map - Array of ColorTypes.RGBA{Float64,1} giving the rgb colour map.

     If returnname=true the function additionally returns
         name - A string giving a nominal name for the colour map
         desc - A string giving a brief description of the colour map
```

Usage 3 and 4:  cmap(searchStr)

Given the large number of colour maps that this function can create this usage option provides some help by listing the numbers of all the colour maps with names containing the string 'str'.  Typically this is used to search for colour maps having a specified attribute: "linear", "diverging", "rainbow", "cyclic", or "isoluminant" etc.  If 'searchStr' is omitted all colour maps are listed.

```
   cmap()              # lists all colour maps
   cmap("diverging")   # lists all diverging colour maps
```

Note the listing of colour maps can be a bit slow because each colour map has to be created in order to determine its full name.

**Using the colour maps:**

PyPlot:

```
> using PyPlot
> sr = sineramp();    # Generate the sineramp() colour map test image.
> imshow(sr);         # Display with matplotlib's default 'jet' colour map.
                      # Note the perceptual dead spots in the map.
> imshow(sr, cmap = ColorMap(cmap("L3"))); # Apply the cmap() heat colour map.
```

Plots:

```
> using Plots
> y=rand(100);
> Plots.scatter(y, zcolor=y, marker=ColorGradient(cmap("R3")));
```

You can also apply a colour map to a single channel image to create a conventional RGB image. This is recommended if you are using a diverging or cyclic colour map because it allows you to ensure data values are honoured appropriately when you map them to colours.

```
  Apply the L4 heat colour map to the test image
> rgbimg = applycolourmap(sr, cmap("L4"));

  Apply a diverging colour map to the test image using 127 as the
  value that is associated with the centre point of the diverging
  colour map
> rgbimg = applydivergingcolourmap(sr, cmap("D1"),127);

  Apply a cyclic colour map to the circlesineramp() test image specifying
  a data cyclelength of 2*pi.
> (cr,) = circlesineramp();   # Generate a cyclic colour map test image.
> rgbimg = applycycliccolourmap(cr, cmap("C1"), cyclelength=2*pi);

> ImageView.view(rgbimg)      # Display the image with ImageView
> PyPlot.imshow(rgbimg)       # or with PyPlot
```

*Warning* PyPlot and Tk do not seem to coexist very well (Julia can crash!).  ImageView and Winston use Tk which means that you may have to take care which image display functions you choose to use.

**Colour Map naming convention:**

```
                    linear_kryw_5-100_c67_n256
                      /      /    |    \    \
  Colour Map attribute(s)   /     |     \   Number of colour map entries
                           /      |      \
     String indicating nominal    |      Mean chroma of colour map
     hue sequence.                |
                              Range of lightness values
```

In addition, the name of the colour map may have cyclic shift information appended to it, it may also have a flag indicating it is reversed.

```
              cyclic_wrwbw_90-40_c42_n256_s25_r
                                          /    \
                                         /   Indicates that the map is reversed.
                                        /
                  Percentage of colour map length
                  that the map has been rotated by.
```

  * Attributes may be: linear, diverging, cyclic, rainbow, or isoluminant.  A

colour map may have more than one attribute. For example, diverging-linear or cyclic-isoluminant.

  * Lightness values can range from 0 to 100. For linear colour maps the two

lightness values indicate the first and last lightness values in the map. For diverging colour maps the second value indicates the lightness value of the centre point of the colour map (unless it is a diverging-linear colour map). For cyclic and rainbow colour maps the two values indicate the minimum and maximum lightness values. Isoluminant colour maps have only one lightness value.

  * The string of characters indicating the nominal hue sequence uses

the following code

```
      r - red      g - green      b - blue
      c - cyan     m - magenta    y - yellow
      o - orange   v - violet
      k - black    w - white      j - grey
```

('j' rhymes with grey). Thus a 'heat' style colour map would be indicated by the string 'kryw'. If the colour map is predominantly one colour then the full name of that colour may be used. Note these codes are mainly used to indicate the hues of the colour map independent of the lightness/darkness and saturation of the colours.

  * Mean chroma/saturation is an indication of vividness of the colour map. A

value of 0 corresponds to a greyscale. A value of 50 or more will indicate a vivid colour map.

Adding your own colour maps is straightforward. See comments within the code for instructions for doing this.

Reference: Peter Kovesi. Good Colour Maps: How to Design Them. [arXiv:1509.03700 [cs.GR] 2015](https://arXiv:1509.03700)

See also: equalisecolourmap, viewlabspace, sineramp, circlesineramp, applycolourmap, applycycliccolourmap, applydivergingcolourmap
