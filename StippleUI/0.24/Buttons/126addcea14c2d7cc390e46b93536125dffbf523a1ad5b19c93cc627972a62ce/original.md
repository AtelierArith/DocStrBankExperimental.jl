`btndropdown` is a very convenient dropdown button. Goes very well with `list` as dropdown content, but it’s by no means limited to it.

In case you are looking for a dropdown “input” instead of “button” use Select instead.

### Examples

```
julia> btndropdown(label = "Dropdown Button", color = "primary", [
            list([
              item("Spain", clickable = true, vclosepopup = true, @click("first_item = true")),
              item("USA", clickable = true, vclosepopup = true, @click("second_item = true")),
              item("Netherlands", clickable = true, vclosepopup = true, @click("third_item = true"))
            ]),
       ])
```

---

### Arguments

---

1. Behavior

      * `loading::Bool` - Put button into loading state (displays a `spinner` – can be overridden by using a 'loading' slot)
      * `split::Bool` - Split dropdown icon into its own button
      * `disablemainbtn::Bool` - Disable main button (useful along with 'split' prop)
      * `disabledropdown::Bool` - Disables dropdown (dropdown button if using along 'split' prop)
      * `persistent::Bool` - Allows the menu to not be dismissed by a click/tap outside of the menu or by hitting the ESC key
      * `autoclose::Bool` - Allows any click/tap in the menu to close it; Useful instead of attaching events to each menu item that should close the menu on click/tap
2. Content

      * `label::Union{String, Int}` - The text that will be shown on the button ex. `"Button Label"`
      * `icon::String` - Icon name following Quasar convention; Make sure you have the icon library installed unless you are using 'img:' prefix; If 'none' (String) is used as value then no icon is rendered (but screen real estate will still be used for it) ex. `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `iconright::String` - Icon name following Quasar convention; Make sure you have the icon library installed unless you are using 'img:' prefix; If 'none' (String) is used as value then no icon is rendered (but screen real estate will still be used for it) ex. `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
      * `nocaps::Bool` - Avoid turning label text into caps (which happens by default)
      * `nowrap::Bool` - Avoid label text wrapping
      * `align::String`  - Label or content alignment default. `center` ex. `"left"` `"right"` `"center"` `"around"` `"between"` `"evenly"`
      * `stack::Bool` - Stack icon and label vertically instead of on same line (like it is by default)
      * `stretch::Bool` - When used on flexbox parent, button will stretch to parent's height
      * `split::Bool` - Split dropdown icon into its own button
      * `dropdownicon::String` - Icon name following Quasar convention; Make sure you have the icon library installed unless you are using 'img:' prefix; If 'none' (String) is used as value then no icon is rendered (but screen real estate will still be used for it) ex. `"map"` `"ion-add"` `"img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg"` `"img:path/to/some_image.png"`
3. General

      * `type::String` - 1) Define the button native type attribute (submit, reset, button) or 2) render component with <a> tag so you can access events even if disable or 3) Use 'href' prop and specify 'type' as a media tag default. `"button"` ex. `"a"` `"submit"` `"reset"` `"button"` `"image/png"` `href="https://some-site.net" target="_blank"`
      * `tabindex::Union{Int, String}` - Tabindex HTML attribute value ex. `0` `100`
4. Navigation

      * `href::String` - Native <a> link href attribute; Has priority over the 'to' and 'replace' props ex. `"https://quasar.dev"` `href="https://quasar.dev" target="_blank"`
      * `target::String` - Native <a> link target attribute; Use it only with 'to' or 'href' props ex. `"_blank"` `"_self"` `"_parent"` `"_top"`
5. Position

      * `cover::Bool` - Allows the menu to cover the button. When used, the 'menu-self' and 'menu-fit' props are no longer effective
      * `menuanchor::String` - Two values setting the starting position or anchor point of the menu relative to its target default. `"bottom end"` ex. `"top start"` `"bottom start"` `"top end"` `"bottom end"` `"right start"` `"right end"` `"left start"` `"left end"`
      * `menuself::String` - Two values setting the menu's own position relative to its target default. `"top end"` ex. `"top start"` `"bottom start"` `"top end"` `"bottom end"` `"right start"` `"right end"` `"left start"` `"left end"`
      * `menuoffset::Vector` - An array of two numbers to offset the menu horizontally and vertically in pixels ex. `[8,8]` `[5,10]`
6. State

      * `loading::Bool` - Put button into loading state (displays a `spinner` – can be overridden by using a 'loading' slot)
      * `disable::Bool` - Put compontent in disabled state
7. Style

      * `size::String` - Size in CSS units or percentage, ex. `"25px"` `"2.5em"` `"md"` `"xs"`
      * `ripple::Union{Bool, Dict}` - Configure material ripple (disable it by setting it to 'false' or supply a config object) default. `true` ex. `false` `{ "early" => true, "center" => true, "color" => "teal", "keyCodes" => []}`
      * `outline::Bool` - Use 'outline' design
      * `flat::Bool` - Use 'flat' design
      * `unelevated::Bool` - Remove shadow
      * `rounded::Bool` - Applies a more prominent border-radius for a squared shape button
      * `push::Bool` - Use 'push' design
      * `glossy::Bool` - Applies a glossy effect
      * `fab::Bool` - Makes button size and shape to fit a Floating Action Button
      * `fabmini::Bool` - Makes button size and shape to fit a Floating Action Button Mini
      * `padding::String` - Apply custom padding (vertical [horizontal]); Size in CSS units, including unit name or standard size name (none|xs|sm|md|lg|xl); Also removes the min width and height when set ex. `"16px"`,`"2rem"` ,`"xs"` ,`"md lg"` ,`"2px 2px 5px 7px"`
      * `color::String` - Color name for component from the [Quasar Color Palette](https://quasar.dev/options/color-palette) ex. `"primary"` `"teal-10"`
      * `textcolor::String` - Overrides text color (if needed); Color name from the [Quasar Color Palette](https://quasar.dev/options/color-palette) ex. `"white"` `"primary"` `"teal-10"`
      * `dense::Bool` - Dense mode; occupies less space
      * `noiconanimation::Bool` - Disables the rotation of the dropdown icon when state is toggled
      * `contentstyle::Union{Vector, String, Dict}` - Style definitions to be attributed to the menu ex. `{"background-color" => "#ff0000"}` `contentclass!="{ 'my-special-class': <condition> }"`
      * `contentclass::Union{Vector, String, Dict}` - Class definitions to be attributed to the menu ex. `"my-special-class"` `contentclass!="{ 'my-special-class': <condition> }"`
