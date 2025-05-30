`@spinner`: Command line spinners with Unicode support

Usage: `@spinner [style] [rate] [message] function`

  * `style`: `String`, `Vector{String}`, or `Symbol`

      * See `Spinners.list` for the list of supported symbols
  * `rate`: seconds per frame
  * `message::String`: text displayed to the right of the spinner

Examples:

```
	@spinner
	@spinner :aesthetic
	@spinner "◧◨" 0.5 sleep(5)
```
