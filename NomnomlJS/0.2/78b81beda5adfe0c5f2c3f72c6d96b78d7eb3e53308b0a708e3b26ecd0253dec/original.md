The `NomnomlJS` package provides an interface to the `nomnoml` JavaScript library for rendering UML diagrams from `.noml` strings and via the `read(filename, Diagram)` overload.

The public interface for this package is the `Diagram` type, which constructs a `nomnoml` diagram. This object can then be written to several different file formats via `write(filename, diagram)`.

The following list of support syntax and features is quoted from the upstream repository, [nomnoml](https://github.com/skanaar/nomnoml):

### Association types

```plaintext
-    association
->   association
<->  association
-->  dependency
<--> dependency
-:>  generalization
<:-  generalization
--:> implementation
<:-- implementation
+-   composition
+->  composition
o-   aggregation
o->  aggregation
--   note
-/-  hidden
_>   weightless edge
__   weightless dashed edge
```

### Classifier types

```plaintext
[name]
[<abstract> name]
[<instance> name]
[<reference> name]
[<note> name]
[<package> name]
[<frame> name]
[<database> name]
[<start> name]
[<end> name]
[<state> name]
[<choice> name]
[<sync> name]
[<input> name]
[<sender> name]
[<receiver> name]
[<transceiver> name]
[<actor> name]
[<usecase> name]
[<label> name]
[<hidden> name]
[<table> name| a | 5 || b | 7]
```

### Directives

```plaintext
#import: my-common-styles.nomnoml
#arrowSize: 1
#bendSize: 0.3
#direction: down | right
#gutter: 5
#edgeMargin: 0
#gravity: 1
#edges: hard | rounded
#background: transparent
#fill: #eee8d5; #fdf6e3
#fillArrows: false
#font: Calibri
#fontSize: 12
#leading: 1.25
#lineWidth: 3
#padding: 8
#spacing: 40
#stroke: #33322E
#title: filename
#zoom: 1
#acyclicer: greedy
#ranker: network-simplex | tight-tree | longest-path
```

### Custom classifier styles

A directive that starts with "." define a classifier style. The style is written as a space separated list of modifiers and key/value pairs.

```plaintext
#.box: fill=#8f8 dashed
#.blob: visual=ellipse title=bold
[<box> GreenBox]
[<blob> HideousBlob]
```

Modifiers

```plaintext
dashed
empty
```

Key/value pairs

```plaintext
fill=(any css color)

stroke=(any css color)

align=center
align=left

direction=right
direction=down

visual=actor
visual=class
visual=database
visual=ellipse
visual=end
visual=frame
visual=hidden
visual=input
visual=none
visual=note
visual=package
visual=receiver
visual=rhomb
visual=roundrect
visual=sender
visual=start
visual=table
visual=transceiver
```

Style title and text body with a comma separated list of text modifiers

```plaintext
title=left,italic,bold
body=center,italic,bold
```

Text modifiers

```plaintext
bold
center
italic
left
underline
```
