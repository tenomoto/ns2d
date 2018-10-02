# はじめに


[Software Design 2018年10月号](https://gihyo.jp/magazine/SD/archive/2018/201810)掲載『平林万能IT技術研究所 地球のどこでも「この瞬間に街を流れる風」を可視化せよ！』では，建物の周りの風を2次元Navier-Stokes方程式を解いて計算している。手順は以下の通りである。

1. [OpenWeatherMap](https://openweathermap.org)から指定した緯度経度近傍の風向・風速データを取得
1. [OpenStreetMap](https://www.openstreetmap.org)を画像処理して流体計算から除く建物マスクを生成
1. 2次元Navier-Stokes方程式ソルバを実行
1. Matplotlibで可視化

あとで述べるように，風向・風速データはアメダスを使っても良いし，自分で指定しても良い。OpenStreetMapには建物のデータが入っていない地域もあるが，基盤地図情報など別の情報からマスクを作成しても良い。このノートブックでは，[CFDPython](https://bitbucket.org/cfdpython/cfd-python-class/overview)に従って，流体ソルバを作成したあと，平林氏の記事に従ってOpenWeatherMap, OpenStreeMapのデータを用いた風の流れを計算する。最後に基盤地図情報とアメダスデータを用いた風の計算について紹介する。

## 参考としたURL

* [CFDPython (bitbucket)](https://bitbucket.org/cfdpython/cfd-python-class/overview): 関連するStep 11がある。
* [CFDPython (github)](https://github.com/barbagroup/CFDPython): 新しいがStep 11がない。
* [hirax/BlowinInTheWindAtAnywhereYouWant](https://github.com/hirax/BlowinInTheWindAtAnywhereYouWant)