# string2map
Parse std::string to std::map

## Objective

Input
- std::[w]string
- Key delimiter (default `=`)
- Value delimiter (default `CRLF`)

Output
- std::map<[w]string,[w]string> or std::unordered_map<[w]string,[w]string>

Converts the input string with the specified delimiters into a map of key-value pairs.

## API

```cpp
namespace string2map
{
    template<typename St, typename Tout>
    Tout parse(St& src);
}
```

## Usage

```cpp
#include <string>
#include <map>

#include <gtest.h>

using namespace std;

TEST(string2map, ParseCheck)
{
    string     sampleStr{ "Host: hostname.com\r\nContent-Type: text\r\nContent-Length: 99\r\n\r\n"s };
    map<string,string>  kvmap{};

    kvmap= string2map::parse(sampleStr);

    EXPECT_EQ(3, kvmap.size());
}
```