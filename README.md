# extension-builder

This is a cloud build system of app inventor extensions

* [Formal server](http://bot.colintree.cn:8048)
* [Dev server](http://bot.colintree.cn:8049)

[Github source](https://github.com/ColinTree/extension-builder)

## How to deploy

In your server, run:

```shell
cd /path/to/extension-builder/
git pull

# if there is already one container running
docker stop extension-builder
docker rm extension-builder

docker build . -t extension-builder
docker run -d -p 8048:8048 --restart unless-stopped --name="extension-builder" extension-builder
```

## How to use

To make extensions enable to be recognised & built by this service, add `builder-config.json` in the same directory of your extension java file.

`builder-config.json` Accepts:

```json
{
  // [Optional] Same package name with your extension(s)
  //            If this is left blank, builder will try to detect from your java files
  "package": @string,
  // [Optional] This will be affective only if the build is called by webhook
  "pushToRelease": @boolean
}
```

Sample config: https://github.com/OpenSourceAIX/ColinTreeListView/blob/master/builder-config.json