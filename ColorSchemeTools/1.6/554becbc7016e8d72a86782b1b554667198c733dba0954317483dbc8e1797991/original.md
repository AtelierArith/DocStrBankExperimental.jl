```
image_to_swatch(imagefilepath, samples, destinationpath;
    nrows=50,
    tilewidth=5)
```

Extract a ColorsSheme from the image in `imagefilepath` to a swatch image PNG in `destinationpath`. This just runs `sortcolorscheme()`, `colorscheme_to_image()`, and `save()` in sequence.

Specify the number of colors. You can also specify the number of rows, and how many times each color is repeated.

```
image_to_swatch("monalisa.jpg", 10, "/tmp/monalisaswatch.png")
```
