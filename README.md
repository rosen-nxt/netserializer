# NetSerializer - A fast, simple serializer for .Net

This version is adapted by Rosenxt

NetSerializer is a simple and very fast serializer for .Net languages. It is
the fastest serializer I have found for my use cases.

The main pros of NetSerializer are:

- Excellent for network serialization
- Supports classes, structs, enums, interfaces, abstract classes
- No versioning or other extra information is serialized, only what is strictly needed
- No type IDs for primitive types, structs or sealed classes, so less data to be sent
- No dynamic type lookup for primitive types, structs or sealed classes, so
  deserialization is faster
- No extra attributes needed (like DataContract/Member), just add the standard
  [Serializable]
- Thread safe without locks
- The data is written to the stream and read from the stream directly, without
  the need for temporary buffers
- With the adaption of Rosenxt it is possible to use the serializer in a dynamic way,
  that each serialized type is added automatically to the type map. So it is not required
  to know exaxtly the types which will be expected. It is only required to provide
  the type map which was created during the serialization to all serializers which are used
  for deserialization

The simpleness of NetSerializer has a drawback which must be considered by the
user: no versioning or other meta information is sent, which means that the
sender and the receiver have to have the same versions of the types being
serialized.

This means that it's a bad idea to save the serialized data for longer periods
of time, as a version upgrade could make the data non-deserializable.

For this reason I think the best (and perhaps only) use for NetSerializer is
for sending data over network, between a client and a server which have
verified version compatibility when the connection is made.

## Documentation

See [Documentation](Doc.md) page.

## Performance

See [Performance](Performance.md) page.
