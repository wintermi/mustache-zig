# MUSTACHE-ZIG

![logo](mustache.png)

Mustache-Zig is an implementation of the [{{mustache}} template system](https://mustache.github.io/) for [Zig](https://ziglang.org/).

# ! Under development !

## Full spec compliant

- Supports most of elements from [mustache spec](https://github.com/mustache/spec) with all tests passing ✔️.

    delimiters
    interpolation
    unescaped interpolation
    sections
    inverted sections
    comments

- Partials and inheritance comming soon ...

    partials
    parent
    blocks

## Designed for low memory consumption.

Mustache templates are well known for HTML templating, but it's useful to render any kind of dynamic document, and potentially load templates from untrusted or user-defined sources.

So, it's important to be able to deal with multi-megabyte inputs without eating all your RAM.

```Zig

    // 16KB should be enough memory for this job
    var plenty_of_memory = std.heap.GeneralPurposeAllocator(.{ .enable_memory_limit = true }){
        .requested_memory_limit = 16 * 1024,
    };
    defer _ = plenty_of_memory.deinit();

    try mustache.renderFromFile(plenty_of_memory.allocator(), data, "10MB_file.mustache", ctx, out_writer);

```

## Samples

- See the source code

## Licensing

- MIT

- Mustache is Copyright (C) 2009 Chris Wanstrath
Original CTemplate by Google