```
    pdOutlineItemGetAttr(item::PDOutlineItem) -> Dict{Symbol, Any}
```

Attributes stored with an `PDOutlineItem` object. The traversal parameters like `Prev`, `Next`, `First`, `Last` and `Parent` are stored with the structure.

The following keys are stored in the dictionary object returned:

  * `:Title` - The title assigned to the item (shows up in the table of content)
  * `:Count` - A representation of no of items open under the outline item. Please

refer to the PDF Spec 32000-2008 section 12.3.2.2 for details. Mostly, used for rendering on a user interface.

  * `:Destination` - `(filepath, PDDestination)` value. Filepath is an empty string

if the destination refers to a location in the same PDF file. This parameter is a combination of `/Dest` and `/A` attribute in the PDF specification. The action element is analyzed and data is extracted and stored with the `PDDestination` as the final refered location.

  * `:C` - The color of the outline in the `DeviceRGB` space.
  * `:F` - Flags for title text rendering `italic=1`, `bold=2`

# Example

```
    julia> pdOutlineItemGetAttr(outlineitem)
Dict{Symbol,Any} with 5 entries:
  :F           => 0x00
  :Title       => "Table of Contents"
  :Count       => 0
  :Destination => ("", PDDestination(2, /XYZ, Float32[0.0, 0.0, 0.0, 756.0], 0.0))
  :C           => Float32[0.0, 0.0, 0.0]
```
