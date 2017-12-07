# このソフトウェアについて

PythonコードをGoogle翻訳で国際化した。

Babelでpyファイルからpot,po,moファイルを作成する。Google翻訳APIで翻訳したテキストを使う。

`./res/i18n/script/run.py`

msgidを原文として翻訳する。

# 前回

* [Python.i18n.Babel.201709161639](https://github.com/ytyaru/Python.i18n.Babel.201709161639)

## 実行結果

```sh
$ python run.py 
HTTP Code: 200
{'sentences': [{'trans': 'Hello World !!', 'orig': 'Hello World !!', 'backend': 0}], 'src': 'en', 'confidence': 0.7099877, 'ld_result': {'srclangs': ['en'], 'srclangs_confidences': [0.7099877], 'extended_srclangs': ['en']}}
Hello World !!
HTTP Code: 200
{'sentences': [{'trans': 'Good Luck !', 'orig': 'Good Luck !', 'backend': 0}], 'src': 'en', 'confidence': 1, 'ld_result': {'srclangs': ['en'], 'srclangs_confidences': [1], 'extended_srclangs': ['en']}}
Good Luck !
HTTP Code: 200
{'sentences': [{'trans': 'Hallo Welt !!', 'orig': 'Hello World !!', 'backend': 1}], 'src': 'en', 'confidence': 0.7099877, 'ld_result': {'srclangs': ['en'], 'srclangs_confidences': [0.7099877], 'extended_srclangs': ['en']}}
Hallo Welt !!
HTTP Code: 200
{'sentences': [{'trans': 'Viel Glück !', 'orig': 'Good Luck !', 'backend': 1}], 'src': 'en', 'confidence': 1, 'ld_result': {'srclangs': ['en'], 'srclangs_confidences': [1], 'extended_srclangs': ['en']}}
Viel Glück !
HTTP Code: 200
{'sentences': [{'trans': 'こんにちは世界 ！！', 'orig': 'Hello World !!', 'backend': 1}, {'translit': "Kon'nichiwa sekai! !"}], 'src': 'en', 'confidence': 0.7099877, 'ld_result': {'srclangs': ['en'], 'srclangs_confidences': [0.7099877], 'extended_srclangs': ['en']}}
こんにちは世界 ！！
HTTP Code: 200
{'sentences': [{'trans': 'がんばろう ！', 'orig': 'Good Luck !', 'backend': 1}, {'translit': 'Ganbarou!'}], 'src': 'en', 'confidence': 1, 'ld_result': {'srclangs': ['en'], 'srclangs_confidences': [1], 'extended_srclangs': ['en']}}
がんばろう ！
```

# 課題

* pot, po, moファイルの更新を実装する（現在は新規作成のみ）
    * 新規追加、変更、の箇所は新たに翻訳処理を行う
* 翻訳リクエスト回数を減らす工夫をする
    * 原文言語と翻訳言語が同一のときは翻訳しないようにする（原文をそのままmessage.stringに代入する）
    * 1回のリクエストに10件分(1000文字分)の文章を入力するなど
* 翻訳リクエスト部分の抽象化
* 異なる翻訳APIの実装

必要性があるか微妙な課題は以下。

* 言語コード文字列の妥当性確認
* 翻訳APIごとにおけるドメイン名の自動分割('domain_google', 'domain_microsoft'等)

# 開発環境

* Linux Mint 17.3 MATE 32bit
* [pyenv](https://github.com/pylangstudy/201705/blob/master/27/Python%E5%AD%A6%E7%BF%92%E7%92%B0%E5%A2%83%E3%82%92%E7%94%A8%E6%84%8F%E3%81%99%E3%82%8B.md) 1.0.10
    * Python 3.6.1
        * [Babel](https://github.com/python-babel/babel) 2.5.1
* Google翻訳API
        
# ライセンス

* https://sites.google.com/site/michinobumaeda/programming/pythonconst

Library|License|Copyright
-------|-------|---------
[Babel](https://github.com/python-babel/babel)|[BSD 3-clause](https://github.com/python-babel/babel/blob/master/LICENSE)|[Copyright (C) 2013 by the Babel Team, see AUTHORS for more information.](https://github.com/python-babel/babel/blob/master/LICENSE)
