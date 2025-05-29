```
textplace(txt::T where T <: AbstractString, pos::Point, params::Vector;
    action = :fill,
    startnewpath = false)
```

A low-level function that places text characters one by one according to the parameters in `params`. First character uses the first tuple, second character uses the second, and so on.

Returns the next text position.

A tuple of parameters is:

```julia
(face = "TimesRoman", size = 12, color=colorant"black", kern = 0, shift = 0, advance = true)
```

where

  * `face` is fontface "string"                   # sticky
  * `size` is fontsize # pts                      # sticky
  * `color` is color                              # sticky
  * `kern` amount (pixels) shifted to the right   # resets after each char
  * `shift` = baseline shifted vertically         # resets after each char
  * `advance` - whether to advance                # resets after each char

Some parameters are "sticky": once set, they apply for all subsequent characters until a new value is supplied. Others aren't sticky, and are reset for each character. So font face, size, and color parameters need only be specified once, whereas kern/shift/advance modifiers are reset for each character.

## Example

Draw the Hogwarts Express Platform number 9 and 3/4:

```julia
txtpos = textplace("93—4!", O - (200, 0), [
    # format for 9:
    (size=120, face="Bodoni-Poster", color=colorant"grey10"),
    # format for 3:
    (size=60,  kern = 5, shift = 60,  advance=false,),
    # format for -:
    (          kern = 0, shift = 25,  advance=false,),
    # format for 4:
    (          kern = 5, shift = -20, advance=true),
    # format for !:
    (size=120, kern = 20,),
    ])
```
