```
quakeml(qml::EventParameters; version="1.2") -> xml::EzXML.XMLDocument
```

Create an XML document from `qml`, a set of events of type `EventParameters`. `xml` is an `EzXML.XMLDocument` suitable for output.

The user may also set the nominal `version` of QuakeML created.

The QuakeML document `xml` may be written with `write(io, xml)` or converted to a string with `string(xml)`.
