```
XML(info::StreamInfo)
```

Return XML document (from LightXML) containing the entire StreamInfo.

This yields an XML document whose top-level element is `<info>`. The info element contains one element for each field of the StreamInfo instance, including:

  * the core elements `<name>`, `<type>`, `<channel_count`, `<nominal_srate>`,  `<channel_format>`, `<source_id>`
  * the misc elements `<version>`, `<created_at>`, `<uid>`, `<session_id>`, `<v4address>`, `<v4data_port>`, `<v4service_port>`, `<v6address>`, `<v6data_port>`, `<v6service_port>`
  * the extended description element `<desc>` with user-defined sub-elements.
