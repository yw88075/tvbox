有缘人注意：本zip目前僅支持"影視","OK影視"使用，其他播放器或基於影視魔改的播放器使用本zip都會導致網盤内容無法播放。對本zip内的核心jar所作的任何魔改、縫合都會導致網盤原畫不可播放。
* 本ZIP所加载的资源完全来自网上公开分享的内容，若有版权问题请联系相关网站删除，本ZIP只读取和播放网络公开资源，既不维护也不储存任何网络资源。

****************************************************************
*  把本zip文件解壓縮到安卓設備的任意目錄                       *
*  然後在播放器的點播接口設定中，指定到解壓後目錄中的jsm.json  *
****************************************************************
* 每次更新zip都可以覆蓋到同一個目錄，覆蓋后無需重新掃碼就可以繼續使用網盤
* 可以使用影視的内部http服務器實現zip上傳和自動解壓，方法：用手機或PC打開http://播放器IP:9978/，
* 然後點擊最後一個TAB(本地)，然後創建一個新文件夾，例如“tvbox”，然後進入"tvbox"，然後創建"js"和"lib"兩個子目錄，
* 然後點擊“上傳檔案”，把本zip上傳到該目錄就會自動解壓。

================================================================
以下所有说明不看也可以正常使用本zip，只是给动手能力强的有缘人更多定制化的可能性。默认设置就可以欣赏绝大部分网络资源，只需要切换到“网盘及弹幕设置”这个视频源扫不同网盘的二维码即可。（切换方法：播放器首页点击左上角图标或文字，找到“网盘及弹幕设置”点击）
================================================================

提示0: 多个播放器或多次外挂本zip情况下，需要只保留一个播放器或1个外挂运行，其他的要主动杀掉，否则可能出现网盘播放异常.
提示1：發現影视壳并不能加载最新的jar，如果遇到jar表現異常，或者最新的jar承諾的功能改進沒有實現，請清除播放殼app的緩存后强杀播放壳后再試，清除方法1：在殼app的設置裏點擊“緩存”，清除方法2：設備的應用管理中，清除殼app的數據及緩存。
提示2：迅雷云盘限制极为严格，不要尝试单账号多用户异地使用，或多线程使用，随时可能封号。
提示3：播放原盘ISO时，可能会呼叫外部播放器，此时需要把原播放器在任务列表中锁定，防止原播放器切入后台被杀掉，具体方法：按任务列表按钮，找到原播放器，点击图标在弹出菜单中选择锁定或点击锁头标志

可以透过配置中的“網盤及彈幕配置”的視頻源來實現快捷方便的獲取32位token及opentoken的功能。

複製lib/tokentemplate.json成爲lib/tokenm.json，并填寫必要的内容

tokenm.json格式説明：
{
"token":"這裏填寫阿里云盤的32位token，也可以不填寫，在播放阿里云盤内容時會彈出窗口，點擊QrCode，用阿里云盤app掃碼",
"open_token":"這裏填寫通過alist或其他openapi提供方申請的aliyun openapi token",
"is_vip":true, //是否是阿里云盤的VIP用戶，設置為true后，使用vip_thread_limit設置的數值來并發加速
"vip_thread_limit":32, //這裏是阿里云盤的轉存原畫并發綫程數
"vip_thread_limit_night":"19-23=10", //這裏是阿里云盤的轉存原畫夜间并發綫程數, 等号前标识夜间时段，等号后标识线程数
"quark_thread_limit":32, //這裏是夸克網盤GO代理的并發協程數或java代理的并發綫程數，若遇到賬號被限制並發數，請將此數值改爲10
"quark_vip_thread_limit":32, //這裏是夸克網盤設置quark_is_vip:true之後的并發綫程數，若遇到賬號被限制并發數，請將此數值改爲10
"quark_thread_limit_night":"19-23=10", //這裏是夸克網盤GO代理的夜间并發協程數或java代理的并發綫程數，若遇到賬號被限制並發數，請將此數值改爲10
"quark_vip_thread_limit_night":"19-23=10", //這裏是夸克網盤設置quark_is_guest:false之後的夜间并發綫程數，若遇到賬號被限制并發數，請將此數值改爲10
"quark_is_guest":false, //本項目設置爲false表示是夸克的VIP或88VIP用戶，使用更快的多綫程加載方式，設置爲true表示是純免費的夸克用戶，使用優化限速的多綫程加載方式
"vod_flags":"4kz|auto", //這裏是播放阿里雲的畫質選項，4kz代表轉存GO原畫,4ko代表轉存Open原畫,其他都代表預覽畫質,可選的預覽畫質包括qhd,fhd,hd,sd,ld，
"quark_flags":"4kz|auto", //這裏是播放夸克網盤的畫質選項，4kz代表轉存原畫（GO原畫），其他都代表轉碼畫質,可選的預覽畫質包括4k,2k,super,high,low,normal
"uc_thread_limit":0,
"uc_is_vip":false,
"uc_flags":"4kz|auto",
"uc_vip_thread_limit":0,
"thunder_thread_limit":0,
"thunder_is_vip":false,
"thunder_vip_thread_limit":0,
"thunder_flags":"4kz",
"aliproxy":"這裏填寫外部的加速代理，用於在盒子性能不夠的情況下，使用外部的加速代理來加速播放，可以不填寫",
"proxy":"這裏填寫用於科學上網的地址，連接openapi或某些資源站可能會需要用到，可以不填寫",
"open_api_url":"https://api.xhofe.top/alist/ali_open/token", //這是alist的openapi接口地址，也可使用其他openapi提供商的地址。
"danmu":true,//是否全局開啓阿里云盤所有csp的彈幕支持，聚合類CSP仍需單獨設置，例如Wogg, Wobg
"quark_danmu":true,//是否全局開啓夸克網盤的所有csp的彈幕支持, 聚合類CSP仍需單獨設置，例如Wogg, Wobg
"quark_cookie":"這裏填寫通過https://pan.quark.cn網站獲取到的cookie，會很長，全數填入即可。"
"uc_cookie":"這裏填寫通過https://drive.uc.cn網站登錄獲取的cookie",
"thunder_username":"這裏填入用戶名或手機號，如果是手機號，記得是類似'+86 139123457'這樣的格式，+86后有空格才對",
"thunder_password":"密碼",
"thunder_captchatoken":"首次使用迅雷網盤時，需要使用app彈出的登陸地址去接碼登錄，並獲取captchaToken，具體方法參考alist網站的文檔:https://alist.nn.ci/zh/guide/drivers/thunder.html",
"pikpak_username":"PikPak網盤的用戶名",
"pikpak_password":"PikPak網盤的密碼",
"pikpak_flags":"4kz",
"pikpak_thread_limit":2,
"pikpak_vip_thread_limit":2,
"pikpak_proxy":"用於科學上網連接PikPak網盤的代理服務器地址",
"pikpak_proxy_onlyapi":false,
"pan115_cookie":"",
"pan115_thread_limit":0,
"pan115_vip_thread_limit":0,
"pan115_is_vip":false,
"pan115_flags":"4kz",
"pan115_auto_delete":true,
"pan115_delete_code":"",
"pan115_speed_limit":0,
"pan115_speed_limit_mobile":10485760,
"pan_order":"ali|quark|uc|115|yd|thunder|pikpak"
}
