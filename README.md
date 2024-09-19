erDiagram
    
    NhanVien {
        MaNV int PK
        TenNV varchar
        NgaySinh date
        GioiTinh varchar
        DiaChi varchar
        SDT varchar
        ChucVu varchar
        Luong decimal
        HinhAnh blob
        TenDangNhap varchar
        MatKhau varchar
    }

    KhachHang {
        MaKH int PK
        TenKH varchar
        SDT varchar
        DiaChi varchar
        DiemTichLuy int
    }

    LoaiKhachHang {
        MaLoaiKH int PK
        TenLoaiKH varchar
        DiemTichLuyToiThieu int
        GiamGia decimal
        UuDaiKhac varchar
        MoTa varchar
    }
    
    HangHoa {
        MaHH int PK
        TenHH varchar
        DonViTinh varchar
        GiaBan decimal
        SoLuongTonKho int
        HinhAnh blob
    }

    LoaiHang {
        MaLoai int PK
        TenLoai varchar
        MoTa varchar
    }

    NhaCungCap {
        MaNCC int PK
        TenNCC varchar
        DiaChi varchar
        SDT varchar
    }

    Ban {
        MaBan int PK
        TenBan varchar
        TrangThai varchar
    }

    KhuVuc {
        MaKV int PK
        TenKV varchar
    }

    HoaDon {
        MaHD int PK
        NgayLap date
        GioLap time
        TongTien decimal
        GiamGia decimal
        HinhThucThanhToan varchar
    }

    ChiTietHoaDon {
        MaHD int PK FK
        MaHH int PK FK
        SoLuong int
        DonGia decimal
        ThanhTien decimal
    }

    PhieuNhap {
        SoPhieuNhap int PK
        NgayNhap date
        TongTien decimal
    }

    ChiTietPhieuNhap {
        SoPhieuNhap int PK FK
        MaHH int PK FK
        SoLuong int
        DonGia decimal
        ThanhTien decimal
    }

    PhieuXuat {
        SoPhieuXuat int PK
        NgayXuat date
        LyDoXuat varchar
    }

    ChiTietPhieuXuat {
        SoPhieuXuat int PK FK
        MaHH int PK FK
        SoLuong int
    }
    
    CaLamViec {
        MaCa int PK
        TenCa varchar
        GioBatDau time
        GioKetThuc time
    }

    ChamCong {
        MaNV int PK FK
        Ngay date PK
        MaCa int PK FK
        GioVao time
        GioRa time
    }

    LuongNhanVien {
        MaNV int PK FK
        Thang int PK
        Nam int PK
        LuongCoBan decimal
        PhuCap decimal
        Thuong decimal
        TongLuong decimal
    }

    KhuyenMai {
        MaKM int PK
        TenKM varchar
        LoaiKhuyenMai varchar
        GiaTriKhuyenMai decimal
        NgayBatDau date
        NgayKetThuc date
        DieuKienApDung varchar
    }

    NhanVien ||--|{ HoaDon : "Lập"
    KhachHang ||--|{ HoaDon : "Mua hàng"
    Ban ||--|{ HoaDon : "Sử dụng"
    HoaDon ||--|{ ChiTietHoaDon : "Có"
    HangHoa ||--|{ ChiTietHoaDon : "Được bán"
    NhaCungCap ||--|{ HangHoa : "Cung cấp"
    LoaiHang ||--|{ HangHoa : "Thuộc loại"
    Ban ||--|| KhuVuc : "Thuộc khu vực"
    NhanVien ||--|{ PhieuNhap : "Lập"
    NhaCungCap ||--|{ PhieuNhap : "Cung cấp"
    PhieuNhap ||--|{ ChiTietPhieuNhap : "Có"
    HangHoa ||--|{ ChiTietPhieuNhap : "Được nhập"
    NhanVien ||--|{ PhieuXuat : "Lập"
    PhieuXuat ||--|{ ChiTietPhieuXuat : "Có"
    HangHoa ||--|{ ChiTietPhieuXuat : "Được xuất"
    NhanVien ||--|{ ChamCong : "Chấm công"
    CaLamViec ||--|{ ChamCong : "Làm việc trong ca"
    NhanVien ||--|{ LuongNhanVien : "Nhận lương"
    KhachHang ||--|| LoaiKhachHang : "Thuộc loại"
    HangHoa ||--|| KhuyenMai : "Tham gia khuyến mãi"

    NhanVien ||--|| CaLamViec : "Làm việc"
    
